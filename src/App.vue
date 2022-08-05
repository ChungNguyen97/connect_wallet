<template>
  <div id="app">
    <header-comp />
    <router-view />
  </div>
</template>

<script>
import HeaderComp from "./components/header.vue";

export default {
  components: {
    HeaderComp,
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
}
</style>
