<template>
  <v-container fluid fill-height class="top-navbar-container">
    <v-toolbar dense floating class="top-navbar">
      <div class="inner-toolbar">
        <v-toolbar-title class="font-weight-medium" id="logo">medoh</v-toolbar-title>
        <v-spacer></v-spacer>
        <div class="navbar-btns">
          <v-btn plain>
            <b>BLOG</b>
          </v-btn>
          <v-btn plain>
            <b>CONTACT US</b>
          </v-btn>
          <v-btn rounded="lg" elevation="2" class="profile-btn">
            Profile
          </v-btn>
        </div>
      </div>
    </v-toolbar>
  </v-container>
</template>

<script setup lang="ts">
//
</script>

<style lang="scss">
$logo-color: rgb(250, 133, 47);
$button-bg-color: $logo-color;

#logo {
  font-family: "poppins", sans-serif;
  color: $logo-color;
  letter-spacing: .025em;
  font-size: 1.875rem;
  line-height: 2.25rem;
  padding: 0;
  margin: 0;
}

.top-navbar-container {
  padding: 0;
} 

.top-navbar {
  background-color: rgba(255, 236, 204, 0.5);
  backdrop-filter: blur(16px);
}

@media screen and (min-width: 960px) {
  .profile-btn {
    background-color: $button-bg-color;
    color: white;
  }

  .top-navbar {
    position: fixed;
    z-index: 10;
  }

  .inner-toolbar {
    display: flex;
    width: 100%;
    margin: 0 10% 0 10%;
  }
}

@media screen and (max-width: 960px) {
  .navbar-btns {
    display: none;
  }

  .top-navbar-container {
    .top-navbar {
      width: 100%;
      padding: 0;
    }

    .logo {
      text-align: center;
    }

  }
}
</style>