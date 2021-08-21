<template>
  <div class="cusin-type">
    {{ cusi }}
  </div>
</template>
<script>
export default {
  name: "Cusin",
  props: {
    cusi: String,
  },
};
</script>
<style scoped>
.cusin-type {
  padding: 2px 8px;
  background-color: #ececec;
  margin: 4px;
  font-size: 0.9rem;
  border-radius: 20px;
  color: #373737;
  cursor: pointer;
  opacity: 0.6;
}
</style>