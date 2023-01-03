<template>
  <div class="container">
    <NavLeft />
    <NavRight />
  </div>
</template>

<script>
import NavLeft from "./NavLeft.vue";
import NavRight from "./NavRight.vue";
export default {
  name: "NavBar",
  components: {
    NavLeft,
    NavRight,
  },
};
</script>

<style scoped>
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;

  margin: 36px 392px 75px 100px;
}
</style>
