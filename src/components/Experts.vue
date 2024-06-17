<template>
    <v-container class="experts-container" fluid>
        <h2>Experts</h2>

        <v-row class="expert-cards">
            <v-col v-for="doctor in featured_experts" :key="doctor.id">
                <v-card height="250" width="200" class="expert-card" :image="doctor.picture_url">
                    <v-card-item class="expert-card-items">
                        <v-card-title class="expert-card-title">{{ doctor.name }}</v-card-title>
                        <v-card-text class="expert-card-subtitle">{{ doctor.specialty }}</v-card-text>
                    </v-card-item>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script setup lang="ts">
import { Ref, ref, onMounted } from 'vue';
import axios from 'axios';
const featured_experts: Ref<{ name: string, specialty: string, location: string, picture_url: string, featured_doctor: boolean, id: number }[]> = ref([]);

const get_featured_videos = () => {
    const featured_experts_url = 'http://localhost:8000/doctor/featured_doctors/';

    axios.get(featured_experts_url)
        .then(response => {
            return response.data;
        })
        .then(data => featured_experts.value = data)
        .catch(error => console.log(error));
};

onMounted(() => get_featured_videos());
</script>

<style lang="scss">
.experts-container {
    display: flex;
    flex-direction: column;
    gap: 24px;
    margin: 0 10% 0 10%;
    width: 80%;

    h2 {
        text-align: center;
    }

    .expert-card {
        position: relative;
        margin: 0 auto;
        border-radius: 16px;
    }

    .expert-cards {
        display: flex;
        justify-content: space-between;
        align-items: center;
        overflow: auto;
    }

    .expert-card-items {
        position: absolute;
        bottom: 0;
        left: 0;
        text-align: center;
        padding: 0;

        .expert-card-title {
            color: rgb(250, 133, 47);
            font-size: 1.5rem;
        }

        .expert-card-subtitle {
            color: white;
            font-size: 1rem;
        }
    }
}
</style>