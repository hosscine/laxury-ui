<template>
  <v-toolbar>
    <v-row>
      <v-col cols="6" sm="4">
        <v-select hide-details :items="items" prepend-inner-icon="mdi-calendar-month"></v-select>
      </v-col>
      <v-col cols="6" sm="8" class="d-flex justify-end align-center">
        <span class="overline d-none d-sm-flex">{{cardGuideText}}</span>
        <v-chip outlined label class="ml-2">
          <v-icon left color="grey darken-1">{{cardIcon}}</v-icon>
          <span class="font-weight-light">{{cardText}}</span>
        </v-chip>
      </v-col>
    </v-row>
  </v-toolbar>
</template>

<script>
export default {
  props: {
    items: Array,
    itemsIcon: String,
    cardGuideText: String,
    cardIcon: String,
    cardText: String
  }
}
</script>