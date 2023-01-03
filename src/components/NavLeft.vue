<template>
  <div class="NavLeft-Container">
    <div class="rectangle"></div>
    <p class="NavLeft-title">নগর জীবন</p>
  </div>
</template>

<script>
export default {
  name: "NavLeft",
};
</script>

<style scoped>
.NavLeft-Container {
  position: relative;
  display: flex;
}

.rectangle {
  width: 4px;
  height: 16px;
  background-color: #343434;
  position: absolute;
  top: 0;
  bottom: 0;
  margin: auto;
}

.NavLeft-title {
  font-size: 26px;
  font-weight: bold;
  color: #343434;
  margin-left: 11px;
}
</style>
