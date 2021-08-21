<template>
  <div class="catagerie">
    <div class="catagerie-name"></div>
    <div class="items">
      <Card v-for="menu in item.restaurantList" :key="menu" :menu="menu" />
    </div>
  </div>
</template>
<script>
import Card from "./Card.vue";
export default {
  name: "All",
  components: {
    Card,
  },
  props: {
    item: Object,
    index: Number,
  },
};
</script>
<style scoped>
.all {
  color: white;
}
</style>