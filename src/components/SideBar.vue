<template>
  <div
    class="cat-item"
    @click="scroll({ string })"
    :class="{ active: a == true }"
  >
    <h3>{{ item.category }}</h3>
    <h4>{{ length }} Restaurants</h4>
  </div>
</template>
<script>
export default {
  name: "SideBar",

  props: {
    item: Object,
    Toggle: Boolean,
  },
  data() {
    return {
      length: 0,
      string: this.item.category,
      a: false,
    };
  },
  created() {
    this.length = this.item.restaurantList.length;
  },
  methods: {
    scroll(id) {
      this.a = !this.a;

      document.getElementById(id).scrollIntoView({
        behavior: "smooth",
      });
    },
  },
};
</script>
<style >
.cat-item {
  padding: 20px;
  text-transform: capitalize;
  cursor: pointer;
  border-bottom: 1px solid #eaeaea;
  transition: all 0.1s ease-in-out;
}
.cat-item:hover {
  background: #434343;
  color: white;
}
.active {
  color: white;
  background: #434343;
}
</style>