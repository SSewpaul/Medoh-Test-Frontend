<template>
    <Navbar />

    <v-main class="home-main">
        <Intro />
        <SearchBar />
        <PopularVideos />
        <v-row class="info-text">
            <v-col>
                <h2>Empowering You To Understand Your Options:</h2>
            </v-col>
            <v-col>
                <p>It's difficult to find the right health information online, especially when trying trying to
                    understand your options. With Medoh, things get easier. We're here to help you learn all the
                    possible ways to improve your health, answer questions you have using Medoh AI and guide you to the
                    providers for treatments you need.</p>
            </v-col>
        </v-row>
    </v-main>
</template>

<script lang="ts">
import Intro from '../components/Intro.vue';
import Navbar from '../components/Navbar.vue';
import PopularVideos from '../components/PopularVideos.vue';
import SearchBar from '../components/SearchBar.vue';
import { defineComponent } from 'vue';

export default defineComponent({

})

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

.info-text {
    margin: 0 10% 0 10%;
}
</style>