<template>
  <div class="card a-hover">
    <Image />
    <div class="card-content">
      <h3>
        {{ menu.name }}
      </h3>
      <div class="tag">
        <Cusin v-for="cusi in cusin" :key="cusi" :cusi="cusi" />
      </div>
      <div class="stats">
        <div class="star" :class="{ green: star > 2 }">
          &star;
          {{ star }}
        </div>
        <div>&#8226;</div>
        <div class="delivery_time">
          {{ menu.delivery_time }}
        </div>
        <div>&#8226;</div>
        <div class="menu-price">
          &#x20B9;
          {{ menu.price_for_two }} FOR TWO
        </div>
      </div>
      <div class="quick-view">Quick View</div>
    </div>
  </div>
</template>
<script>
import Image from "./Image.vue";
import Cusin from "./Cusin.vue";
export default {
  name: "Card",
  props: {
    menu: Object,
  },
  components: {
    Image,
    Cusin,
  },
  data() {
    return {
      cusin: [],
      star: "--",
    };
  },
  created() {
    this.cusin = this.menu.food_types.slice(0, 3);
    this.star = this.menu.ratings;
  },
};
</script>
<style scoped>
.card {
  background-color: #fff;
  border: 1px solid hsla(0, 0%, 100%, 0);
  margin: 8px;
  width: 260px;
  position: relative;
  padding: 16px;
  cursor: pointer;
}

.tag {
  display: -webkit-flex;
  display: flex;
  -webkit-align-items: center;
  align-items: center;
  -webkit-flex-wrap: wrap;
  flex-wrap: wrap;
  margin-top: 4px;
}
.card-content {
  margin-top: 8px;
  text-align: left;
}
.stats {
  display: -webkit-flex;
  display: flex;
  -webkit-align-items: center;
  align-items: center;
  -webkit-justify-content: space-between;
  justify-content: space-between;
  font-size: 0.9rem;
  color: #979797;
  margin-top: 16px;
}
.star {
  padding: 2px 6px;
  border-radius: 2px;
}
.green {
  background-color: #48c479;
  color: #fff;
}
.quick-view {
  font-size: 1rem;
  border-top: 1px solid #e9e9eb;
  padding-top: 14px;
  margin-top: 14px;
  font-weight: 500;
  text-align: center;
  color: #5d8ed5;
  opacity: 1;
}
.quick-view:hover {
  color: #686b78;
}
.card:hover {
  border-color: #d3d5df;
  box-shadow: 0 4px 7px 0 rgba(218, 220, 230, 0.6);
}
</style>
