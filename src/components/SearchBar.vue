<template>
    <v-card flat id="search-container">
        <v-card-text>
            <div class="search-bar-container">
                <v-text-field class="search-box" v-model="query" label="Enter question" variant="underlined" single-line @keyup="title_lookup"></v-text-field>

                <v-btn rounded="lg" elevation="2" class="search-btn" prepend-icon="mdi-magnify">Search</v-btn>

            </div>
        </v-card-text>
    </v-card>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    data() {
        return {
            query: '',
        }
    },
    methods: {
        title_lookup() {
            console.log(this.query);
        }
    }
})
</script>

<style lang="scss">
$search-btn-color: rgba(250, 133, 47, 0.7);

#search-container {
    width: 100%;
    background-color: inherit;

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
</style>