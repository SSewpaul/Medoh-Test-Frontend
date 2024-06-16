<template>
    <v-card class="intro-text" flat>
        <v-card-title class="text-h3 text-center" id="intro-title">Answering your questions on rotator cuff injuries
            or tears</v-card-title>
        <v-card-subtitle class="text-center" id="intro-subtitle">
            Submit a question, and we'll provide you a video response from a doctor explaining the answer
        </v-card-subtitle>
    </v-card>
</template>

<style lang="scss">
.intro-text {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 24px;
    width:80%;
    background-color: inherit;

    #intro-title,
    #intro-subtitle {
        text-wrap: balance;
    }

    #intro-subtitle {
        font-size: 1.5rem;
    }
}
</style>