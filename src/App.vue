<template>
  <div class="container">
    <div class="sidebar">
      <div class="sidebar-content">
        <SideBar
          @click="Toggle = false"
          v-for="item in items"
          :key="item"
          :item="item"
          :Toggle="Toggle"
        />
        <div class="cat-item">
          <h3>Only In swiggy</h3>
          <h4>20 Restaurants</h4>
        </div>
        <div class="cat-item" @click="Toggle = !Toggle">
          <h3>All Items</h3>
          <h4>56 Restaurants</h4>
        </div>
      </div>
    </div>
    <div class="wrap">
      <div class="all" v-if="Toggle">
        <div class="catagerie-name">
          <h2 class="catName">All Items</h2>
        </div>
        <All
          v-for="(item, index) in items"
          :key="item"
          :item="item"
          :index="index"
        />
      </div>
      <div class="a" v-if="!Toggle">
        <Categeries
          v-for="(item, index) in items"
          :key="item"
          :item="item"
          :index="index"
        />

        <div class="catagerie-name">
          <h2 class="catName">Only In swiggy</h2>
        </div>
        <Exclusive
          v-for="(item, index) in items"
          :key="item"
          :item="item"
          :index="index"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Categeries from "./components/Catageres.vue";
import SideBar from "./components/SideBar.vue";
import All from "./components/All.vue";
import Exclusive from "./components/Exclusive.vue";
export default {
  name: "App",
  components: {
    Categeries,
    SideBar,
    All,
    Exclusive,
  },
  data() {
    return {
      items: [],
      all: [],
      Toggle: false,
    };
  },
  created() {
    axios
      .get("https://mocki.io/v1/3fb1488d-bbdb-4ddd-9a03-a0d2efc98597")
      .then((response) => {
        this.items = response.data;
        console.log(this.items);
      })
      .catch((error) => {
        console.log("there was an error :" + error.response);
      });
  },
};
</script>

<style>
.container {
  width: 100%;
  max-width: 1200px;
  margin: auto;
  padding: 0 32px;
  display: -webkit-flex;
  display: flex;
  -webkit-justify-content: space-between;
  justify-content: space-between;
  position: relative;
}
.sidebar {
  width: 250px;
  background-color: #fff;
  text-align: left;
}
.sidebar-content {
  position: sticky;
  top: 100px;
  border-top: 1px solid #eaeaea;
  border-left: 1px solid #eaeaea;
  border-right: 1px solid #eaeaea;
}
.wrap {
  max-width: calc(100% - 250px);
}
</style>
