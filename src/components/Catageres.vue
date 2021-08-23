<template>
  <div class="catagerie">
    <div class="catagerie-name">
      <h2 class="catName">{{ item.category }}</h2>
    </div>

    <div class="items">
      <Card v-for="menu in farray" :key="menu" :menu="menu" />
    </div>
    <button @click="add()">show more items</button>
  </div>
</template>
<script>
import Card from "./Card.vue";
export default {
  name: "Categeries",
  components: {
    Card,
  },
  props: {
    item: Object,
    index: Number,
  },

  data() {
    return {
      categoryName: this.item.category,
      itemToShow: 6,
      totalitems: 0,
      farray: [],
      marray: [],
    };
  },
  created() {
    this.farray = this.item.restaurantList.slice(0, this.itemToShow);
  },
  methods: {
    async add() {
      const res = await fetch(
        "https://mocki.io/v1/3fb1488d-bbdb-4ddd-9a03-a0d2efc98597"
      );
      const result = await res.json();
      this.all = [...result];
      this.restaurants = result[this.index].restaurantList;

      this.marray = this.restaurants;
      this.farray = this.item.restaurantList.slice(0, this.itemToShow);
      this.itemToShow += 3;
    },
  },
};
</script>
<style >
.catagerie {
  margin-bottom: 100px;
}
.catagerie-name {
  font-size: 24px;
  text-align: left;
  text-transform: capitalize;
  margin: 0 32px;
  font-weight: 500;
}
.items {
  display: -webkit-flex;
  display: flex;
  -webkit-flex-wrap: wrap;
  flex-wrap: wrap;
  max-width: 100%;
  margin: 8px;
}
button {
  color: #fff !important;
  text-transform: uppercase;
  text-decoration: none;
  background: #656665;
  padding: 20px;
  border-radius: 5px;
  display: inline-block;
  border: none;
  transition: all 0.4s ease 0s;
}
button:hover {
  background: #434343;
  letter-spacing: 1px;
  -webkit-box-shadow: 0px 5px 40px -10px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 0px 5px 40px -10px rgba(0, 0, 0, 0.57);
  box-shadow: 5px 40px -10px rgba(0, 0, 0, 0.57);
  transition: all 0.4s ease 0s;
}
</style>