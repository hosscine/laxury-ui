<template>
  <!-- <v-select prepend-inner-icon="mdi-calendar-month" :items="billMonths"></v-select> -->
  <v-container fluid>
    <v-row align="center">
      <v-col cols="12" class="py-0">
        <v-toolbar class="elevation-2">
          <v-col cols="6">
            <v-select hide-details :items="billMonths" prepend-inner-icon="mdi-calendar-month"></v-select>
          </v-col>
          <v-col cols="6" class="d-flex justify-end align-center">
            <span class="overline d-none d-sm-flex">Current Payment per Person</span>
            <v-chip outlined label active="false" class="ml-2">
              <v-icon left color="grey darken-1">mdi-cash</v-icon>
              <span class="font-weight-light">¥{{singlePayment}}</span>
            </v-chip>
          </v-col>
        </v-toolbar>
      </v-col>

      <v-col cols="6" class="pr-0 pt-0">
        <RemovableTable v-bind:headers="headers" v-bind:items="billShared" sort-by="amount">
          <template v-slot:top></template>
        </RemovableTable>
      </v-col>
      <v-col cols="6" class="pl-0 pt-0">
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
    billMonths: ["2019/10", "2019/11"],
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
    },
    singlePayment() {
      return this.billShared.reduce((a, item) => a + item.amount, 0);
    }
  },

  methods: {}
};
</script>