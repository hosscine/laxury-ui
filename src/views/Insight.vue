<template>
  <v-container>
    <h1>インサイト画面</h1>
    <v-row>
      <v-col class="pr-0">
        <RemovableTable
          v-bind:headers="headers"
          v-bind:items="billShared"
          sort-by="amount"
          class="elevation-1"
        >
          <template v-slot:top></template>
        </RemovableTable>
      </v-col>
      <v-col class="pl-0">
        <RemovableTable
          v-bind:headers="headers"
          v-bind:items="billUnshared"
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
        date: 24,
        shared: true
      },
      {
        name: "Ice cream sandwich",
        amount: 237,
        date: 37,
        shared: true
      },
      {
        name: "Eclair",
        amount: 262,
        date: 23,
        shared: true
      },
      {
        name: "Cupcake",
        amount: 305,
        date: 67,
        shared: true
      },
      {
        name: "Gingerbread",
        amount: 356,
        date: 49,
        shared: true
      },
      {
        name: "Jelly bean",
        amount: 375,
        date: 94,
        shared: false
      },
      {
        name: "Lollipop",
        amount: 392,
        date: 98,
        shared: false
      },
      {
        name: "Honeycomb",
        amount: 408,
        date: 87,
        shared: false
      },
      {
        name: "Donut",
        amount: 452,
        date: 51,
        shared: false
      },
      {
        name: "KitKat",
        amount: 518,
        date: 65,
        shared: false
      }
    ]
  }),

  computed: {
    billShared() {
      return this.bill.filter(item => item.shared);
    },
    billUnshared() {
      return this.bill.filter(item => !item.shared);
    }
  },

  methods: {}
};
</script>