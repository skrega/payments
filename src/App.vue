<template>
  <div id="app">
    <div class="wrapper">
      <header>
        <div class="title">My personal costs</div>
        <button @click="show = !show">add new cost +</button>
      </header>
      <main>
        <add-payment-form
          @addNewPayment="addToPaymentList"
          @clear="PaymentsList = []"
          v-show="show"
        />
        <payments-dispaly :items="PaymentsList" />
      </main>
    </div>
  </div>
</template>

<script>
import AddPaymentForm from "./components/AddPaymentForm.vue";
import PaymentsDispaly from "./components/PaymentsDispaly.vue";

export default {
  components: { PaymentsDispaly, AddPaymentForm },
  name: "App",

  data() {
    return {
      show: false,
      PaymentsList: [],
    };
  },
  methods: {
    fetchData() {
      return [
        {
          date: "28.03.2020",
          category: "Sports",
          value: 169,
        },
        {
          date: "24.03.2020",
          category: "Transport",
          value: 36,
        },
        {
          date: "24.03.2020",
          category: "Food",
          value: 532,
        },
      ];
    },
    addToPaymentList(data) {
      //data это название может быть любое
      //this.PaymentsList.push(data);
      this.PaymentsList = [...this.PaymentsList, data];
    },
  },

  created() {
    this.PaymentsList = this.fetchData();
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
