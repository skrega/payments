<template>
  <div class="wrapper">
    <input type="text" placeholder="date" v-model="date" />
    <input type="text" placeholder="category" v-model="category" />
    <input type="number" placeholder="value" v-model.number="value" />
    <button @click="onClick">Save</button>
    <!-- <button @click="$emit('clear')">Clear</button> -->
  </div>
</template>

<script>
export default {
  name: "AddPaymentForm",
  data() {
    return {
      date: "",
      category: "",
      value: "",
    };
  },
  computed: {
    getCurrentDate() {
      const today = new Date();
      const d = today.getDate();
      const m = today.getMonth() + 1;
      const y = today.getFullYear();
      return `${d}.${m}.${y}`;
    },
  },
  methods: {
    onClick() {
      const data = {
        //наша дата,
        date: this.date || this.getCurrentDate,
        category: this.category,
        value: this.value,
      };
      this.$emit("addNewPayment", data); //от ребенка к родителю
    },
  },
};
</script>

<style>
</style>