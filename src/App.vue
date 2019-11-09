<template>
  <v-app>
    <v-app-bar
      app
      color="black"
      dark
      height="60px"
    >
      <div class="d-flex align-center">
        <v-img
          alt="Luxury Logo"
          class="shrink mr-2"
          contain
          src="https://pbs.twimg.com/profile_images/938212111615893504/CWOlo6Q6_400x400.jpg"
          transition="scale-transition"
          width="50"
          height="50"
        />

        <h1 class="d-none d-sm-flex">Laxury Insight</h1>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://myluxurycard.co.jp"
        target="_blank"
        text
      >
        <span class="mr-2">Laxury Card Online</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <router-view />
    </v-content>
  </v-app>
</template>
