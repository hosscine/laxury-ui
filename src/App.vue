<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Luxury Logo"
          class="shrink mr-2"
          contain
          src="https://pbs.twimg.com/profile_images/938212111615893504/CWOlo6Q6_400x400.jpg"
          transition="scale-transition"
          width="40"
        />

        <h1>Laxury Insight</h1>
      </div>

      <!-- <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn> -->
    </v-app-bar>

    <v-content>
      <router-view />
    </v-content>
  </v-app>
</template>
