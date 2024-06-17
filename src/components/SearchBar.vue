<template>
    <div class="search-container">
        <v-card flat id="search-card">
            <v-card-text>
                <div class="search-bar-container">
                    <v-text-field class="search-box" v-model="query" label="Enter question" variant="outlined"
                        single-line rounded="xl" color="#b03c21"></v-text-field>
                </div>
            </v-card-text>
        </v-card>

        <v-col class="search-results">
            <v-row v-for="item in search_results" :key="item.id" class="result-row">
                <v-btn flat rounded="0" width="100%" :href="item.video_url" class='search-result-btn'>{{ item.title
                    }}</v-btn>
            </v-row>
        </v-col>
    </div>
</template>

<script setup lang="ts">
import { Ref, ref, watch } from 'vue';
import debounce from 'lodash.debounce';
import axios from 'axios';

const query: Ref<string> = ref('');
const search_results: Ref<{ id: number, title: string, video_url: string, thumbnail_url: string, video_type: string, doctor_id: number, popular_video: boolean, featured_video: boolean }[]> = ref([]);

const search = (new_response, old_response) => {
    const search_url = 'http://localhost:8000/video/search/' + query.value;

    if (!new_response) {
        search_results.value = [];
        return;
    }

    axios.get(search_url)
        .then(response => {
            return response.data;
        })
        .then(data => search_results.value = data)
        .catch(error => console.log(error));
}

watch(query, debounce(search, 500))
</script>

<style lang="scss">
$search-btn-color: rgba(250, 133, 47, 0.7);

.search-container {
    width: 100%;
    background-color: inherit;
    position: relative;

    #search-card {
        width: 100%;

        .search-bar-container {
            display: flex;
            align-items: center;
            height: 56px;
            gap: 8px;
            margin: 0 10% 0 10%;

            .search-btn {
                height: 100%;
                background-color: $search-btn-color;
                color: white;
                font-size: larger;
            }

            .search-btn:hover {
                background-color: rgba(250, 133, 47, 1);
            }

            .search-box {
                height: 100%;

                input {
                    font-size: larger;
                }
            }
        }
    }

    .search-results {
        display: none;
    }
}

.search-container:focus-within .search-results {
    display: block;
    position: absolute;
    width: 75%;
    top: 77px;
    left: 12.5%;
    z-index: 5;
    max-height: 400px;
    overflow-y: auto;
    border-radius: 0 0 10px 10px;
    border-top: 0;

    .result-row {
        border-bottom: 1px solid #b03c21;
        background-color: #ffe5cb;
    }

    .search-result-btn {
        background-color: #ffe5cb;
    }

    .result-row:last-child {
        border-bottom: 0;
    }
}
</style>