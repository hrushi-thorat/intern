<template>
  <div class="catagerie">
    <div class="catagerie-name"></div>
    <div class="items">
      <Card v-for="menu in sarray" :key="menu" :menu="menu" />
    </div>
  </div>
</template>
<script>
import Card from "./Card.vue";
export default {
  name: "Exclusive",
  components: {
    Card,
  },
  props: {
    item: Object,
    index: Number,
  },
  data() {
    return {
      sarray: [],
    };
  },
  created() {
    this.sarray = this.item.restaurantList.filter((item) => {
      return item.isExlusive == true;
    });
  },
};
</script>
<style scoped>
.all {
  color: white;
}
</style>