<template>
  <div>
    <NavBar />
  </div>
</template>

<script>
import NavBar from "./components/Navbar.vue";
export default {
  name: "App",
  components: {
    NavBar,
  },
};
</script>

<style>
@import url("https://fonts.cdnfonts.com/css/segoe-ui-4");
* {
  font-family: "Segoe UI", sans-serif;
  margin: 0;
  box-sizing: border-box;
}
</style>
