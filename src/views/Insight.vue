<template>
  <v-container>
    <h1>インサイト画面</h1>
    <v-row>
      <v-col class="pr-0">
        <RemovableTable
          v-bind:headers="headers"
          v-bind:items="items"
          sort-by="amount"
          class="elevation-1"
        >
          <template v-slot:top></template>
        </RemovableTable>
      </v-col>
      <v-col class="pl-0">
        <RemovableTable
          v-bind:headers="headers"
          v-bind:items="items"
          sort-by="amount"
          class="elevation-1"
        >
          <template v-slot:top></template>
        </RemovableTable>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import RemovableTable from "@/components/RemovableTable.vue";

export default {
  components: {
    RemovableTable
  },

  data: () => ({
    headers: [
      {
        text: "Names",
        align: "left",
        sortable: false,
        value: "name"
      },
      { text: "Dates", value: "date" },
      { text: "Amounts", value: "amount" },
      { text: "Actions", value: "action", sortable: false }
    ],
    bill: [
      {
        name: "Frozen Yogurt",
        amount: 159,
        date: 24
      },
      {
        name: "Ice cream sandwich",
        amount: 237,
        date: 37
      },
      {
        name: "Eclair",
        amount: 262,
        date: 23
      },
      {
        name: "Cupcake",
        amount: 305,
        date: 67
      },
      {
        name: "Gingerbread",
        amount: 356,
        date: 49
      },
      {
        name: "Jelly bean",
        amount: 375,
        date: 94
      },
      {
        name: "Lollipop",
        amount: 392,
        date: 98
      },
      {
        name: "Honeycomb",
        amount: 408,
        date: 87
      },
      {
        name: "Donut",
        amount: 452,
        date: 51
      },
      {
        name: "KitKat",
        amount: 518,
        date: 65
      }
    ]
  }),

  computed: {},

  methods: {}
};
</script>