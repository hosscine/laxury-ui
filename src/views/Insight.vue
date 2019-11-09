<template>
  <v-container class="pb-0">
    <v-app-bar class="pa-0 elevation-2" dense>
      <v-row>
        <v-col sm="4" md="6">
          <v-select class="pt-5" prepend-inner-icon="mdi-calendar-month"></v-select>
        </v-col>
        <v-col>

        </v-col>
      </v-row>
    </v-app-bar>
    <v-row>
      <v-col class="pr-0 pt-0">
        <RemovableTable v-bind:headers="headers" v-bind:items="billShared" sort-by="amount">
          <template v-slot:top></template>
        </RemovableTable>
      </v-col>
      <v-col class="pl-0 pt-0">
        <RemovableTable v-bind:headers="headers" v-bind:items="billUnshared" sort-by="amount">
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
        shared: true,
        added: true
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
        shared: true,
        added: true
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

  created() {
    this.bill.forEach((item, index) => {
      if (item.added) this.$set(this.bill[index], "icon", "mdi-delete");
      else
        this.$set(
          this.bill[index],
          "icon",
          item.shared ? "mdi-arrow-right" : "mdi-arrow-left"
        );
    });
  },

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