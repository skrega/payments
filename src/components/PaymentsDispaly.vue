<template>
  <div class="wrapper">
    <ul class="items">
      <li class="item" v-for="(item, idx) in items" :key="idx">
        {{ item.date }}
        {{ item.category }}
        {{ item.value }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "paymentsDisplay",
  //данные которые будем передовать, есть вторая записть в виде массва  props:[]
  props: {
    items: {
      type: Array,
      default: () => [], //по умолчанию возращает пустой массив
    },
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}
.items {
  list-style: decimal;
}
</style>