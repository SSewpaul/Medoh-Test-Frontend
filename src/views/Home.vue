<template>
    <Navbar />

    <v-main class="home-main">
        <Intro />
        <SearchBar />
        <PopularVideos />
        <Info />
        <Topics />
    </v-main>
</template>

<script setup lang="ts">
import Info from '../components/Info.vue';
import Intro from '../components/Intro.vue';
import Navbar from '../components/Navbar.vue';
import PopularVideos from '../components/PopularVideos.vue';
import SearchBar from '../components/SearchBar.vue';
import Topics from '../components/Topics.vue';

</script>

<style lang="scss">
$font-name: "poppins", sans-serif;

.home-main {
    font-family: $font-name;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 104px;
    overflow: auto;
    gap: 40px;
}

</style>