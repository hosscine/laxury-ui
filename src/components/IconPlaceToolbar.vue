<template>
  <v-toolbar dense>
    <v-row justify="start" class="align-center">
      <v-col cols="1" sm="2">
        <v-img :src="require('@/assets/friendship.svg')" contain :height="imgHeight"></v-img>
      </v-col>
      <v-col>
        {{firstText}}
        <span class="d-none d-sm-inline">{{secondText}}</span>
      </v-col>
    </v-row>
  </v-toolbar>
</template>

<script>
export default {
  props: {
    img: Object,
    imgHeight: String,
    firstText: String,
    secondText: String
  }
}
</script>>