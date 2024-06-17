<template>
    <v-container class="topics" fluid>
        <h2>Topics</h2>

        <v-row class="topics-cards">
            <v-col v-for="name in topic_names" :key="name">
                <v-card height="150" width="250" class="topic-card">
                    <v-card-title class="topic-card-title">{{ name }}</v-card-title>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script setup lang="ts">
const topic_names = ["Basics", "Symptoms", "Treatments", "Compilations"]
</script>

<style lang="scss">
.topics {
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

    .topics-cards {
        display: flex;
        flex-wrap: nowrap;
        overflow: auto;
    }

    .topic-card {
        background-image: linear-gradient(to left, #fec389, #ffca96, #ffd2a4, #ffd7ae, #ffdcb7);
        margin: 0 auto;
        border-radius: 16px;
        position: relative;

        .topic-card-title {
            position: absolute;
            bottom: 0;
            left: 50%;
            -webkit-transform: translateX(-50%);
            -moz-transform: translateX(-50%);
            transform: translateX(-50%);
        }
    }
}
</style>