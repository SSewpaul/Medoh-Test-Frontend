<template>
    <v-container class="popular-searches" fluid>
        <h2>Popular Searches</h2>
        <div class="popular-videos">
            <v-col v-for="details in featured_videos" :key="details.title">
                <div class="inner-popular-video-container">
                    <v-btn icon="mdi-play" class="play-btn" :href="details.video_url"></v-btn>
                    <v-card width="250" height="275" class="popular-video-card">
                        <v-img :src="details.thumbnail_url" width="250" height="200" cover class="thumbnail"></v-img>
                        <v-card-item>
                            <v-card-title class="popular-video-title">
                                {{ details.title }}
                            </v-card-title>
                            <v-card-text class="popular-video-metadata">
                                <p class="popular-video-creator">{{ details.doctor_name }}</p>

                                <v-chip class="popular-video-injury-type">
                                    {{ details.video_type }}
                                </v-chip>
                            </v-card-text>
                        </v-card-item>
                    </v-card>
                </div>
            </v-col>
        </div>
    </v-container>
</template>

<script setup lang="ts">
import { Ref, ref, onMounted } from 'vue';
import axios from 'axios';

const featured_videos: Ref<{ id: number, title: string, video_url: string, thumbnail_url: string, video_type: string, doctor_name: string, popular_video: boolean, featured_video: boolean }[]> = ref([]);

const get_featured_videos = () => {
    const featured_videos_url = 'http://localhost:8000/video/featured_videos/';

    axios.get(featured_videos_url)
        .then(response => {
            return response.data;
        })
        .then(data => featured_videos.value = data)
        .catch(error => console.log(error));
};

onMounted(() => get_featured_videos());

</script>

<style lang="scss">
.popular-searches {
    margin-left: 10%;
    margin-right: 10%;
    width: 80%;
    padding: 0;
    display: flex;
    flex-direction: column;
    gap: 24px;

    h2 {
        text-align: center;
    }

    .popular-video-card {
        background-image: linear-gradient(to left, #fec389, #ffca96, #ffd2a4, #ffd7ae, #ffdcb7);
        margin: 0 auto;
        border-radius: 16px;
    }

    .popular-video-title {
        font-size: 1.2rem;
        line-height: 1.2rem;
        padding-bottom: 8px;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .popular-videos {
        display: flex;
        flex-wrap: nowrap;
        overflow: auto;
    }

    .play-btn {
        display: none;
    }

    .popular-video-metadata {
        display: flex;
        align-items: center;
        justify-content: space-between;


    }

    .inner-popular-video-container {
        position: relative;
    }

    .inner-popular-video-container:hover {
        .play-btn {
            display: block;
            position: absolute;
            left: 50%;
            -webkit-transform: translateX(-50%);
            -moz-transform: translateX(-50%);
            transform: translateX(-50%);
            bottom: 140px;
            z-index: 2;
            background-color: #fff5e5;
            color: #fb552f;
            width: 80px;
            height: 80px;
            font-size: 50px;
        }

        .popular-video-card {
            filter: blur(1px);
        }
    }
}
</style>