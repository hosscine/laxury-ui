<template>
  <!-- <v-select prepend-inner-icon="mdi-calendar-month" :items="billMonths"></v-select> -->
  <v-container fluid>
    <v-row align="center">
      <v-col cols="12" class="py-0">
        <SelectItemToolbar
          :items="billMonths"
          itemsIcon="mdi-calendar-month"
          :cardText="'¥ ' + String(singlePayment)"
          cardGuideText="Payment for each Person"
          cardIcon="mdi-cash"
        />
      </v-col>

      <v-col cols="6" class="pr-0 pt-0">
        <RemovableTable :headers="headers" :items="billShared" sort-by="amount">
          <template v-slot:top>
            <IconPlaceToolbar
              class="elevation-1"
              :src="imageFriend"
              imgHeight="30"
              firstText="Shared"
              secondText="Expense"
            />
          </template>
        </RemovableTable>
      </v-col>
      <v-col cols="6" class="pl-0 pt-0">
        <RemovableTable :headers="headers" :items="billUnshared" sort-by="amount">
          <template v-slot:top>
            <v-toolbar dense class="elevation-1">
              <v-row justify="start" class="align-center">
                <v-col cols="1" sm="2">
                  <v-img :src="require('@/assets/boy.svg')" contain height="30"></v-img>
                </v-col>
                <v-col>
                  Personal
                  <span class="d-none d-sm-inline">Expense</span>
                </v-col>
              </v-row>
            </v-toolbar>
          </template>
        </RemovableTable>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import RemovableTable from "@/components/RemovableTable.vue";
import SelectItemToolbar from "@/components/SelectItemToolbar.vue";
import IconPlaceToolbar from "@/components/IconPlaceToolbar.vue";

export default {
  components: {
    RemovableTable,
    SelectItemToolbar,
    IconPlaceToolbar
  },

  data: () => ({
    billMonths: ["2019/10", "2019/11"],
    imageFriend: require("@/assets/friendship.svg"),
    imageBoy: require("@/assets/boy.svg"),
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