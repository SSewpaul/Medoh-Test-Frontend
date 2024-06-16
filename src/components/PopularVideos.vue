<template>
    <v-container class="popular-searches" fluid>
        <h2>Popular Searches</h2>
        <div class="popular-videos">
            <v-col v-for="details in videos" :key="details.title">
                <div class="inner-popular-video-container">
                    <v-btn icon="mdi-play" class="play-btn"></v-btn>
                    <v-card width="250" height="275" class="popular-video-card">
                        <v-img src="../assets/thumbnail.png" width="250" height="200" cover class="thumbnail"></v-img>
                        <v-card-item>
                            <v-card-title class="popular-video-title">
                                {{ details.title }}
                            </v-card-title>
                            <v-card-text class="popular-video-metadata">
                                <p class="popular-video-creator">{{details.creator}}</p>

                                <v-chip class="popular-video-injury-type">
                                    {{details.injury_type}}
                                </v-chip>
                            </v-card-text>
                        </v-card-item>
                    </v-card>
                </div>
            </v-col>
        </div>
    </v-container>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    data() {
        return {
            videos: {
                0: {
                    'title': 'Can a rotator cuff tear cause numbness in your arm?',
                    'thumbnail': '../assets/thumbnail.png',
                    'creator': 'Didinger',
                    'injury_type': 'rotator cuff'
                },
                1: {
                    'title': 'Most epic injury or something',
                    'thumbnail': '../assets/thumbnail.png',
                    'creator': 'Didinger',
                    'injury_type': 'rotator cuff'
                },
                2: {
                    'title': 'How long can this actually get and what is the problem if we go past the number of characters',
                    'thumbnail': '../assets/thumbnail.png',
                    'creator': 'Didinger',
                    'injury_type': 'rotator cuff'
                },
                3: {
                    'title': 'How long can this actually get and what is the problem if we go past the number of characters',
                    'thumbnail': '../assets/thumbnail.png',
                    'creator': 'Didinger',
                    'injury_type': 'rotator cuff'
                },
                4: {
                    'title': 'How long can this actually get and what is the problem if we go past the number of characters',
                    'thumbnail': '../assets/thumbnail.png',
                    'creator': 'Didinger',
                    'injury_type': 'rotator cuff'
                }
            }
        }
    }
})
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
        max-width: 50ch;
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
            display: inline-block;
            position: absolute;
            right: 85px;
            bottom: 140px;
            z-index: 2;
            background-color: #fff5e5;
            color: #fb552f;
            width: 80px;
            height: 80px;
            font-size: 30px;
        }

        .popular-video-card {
            filter: blur(1px);
        }
    }
}
</style>