<template>
  <div class="home">
    <h3 @click="handleClick" class="intro">Wellcome Fewcha Wallet</h3>
  </div>
</template>

<script>
export default {
  name: "HomeView",

  methods: {
    handleClick() {
      console.log(1);
    },
  },
};
</script>

<style scoped>
.intro {
  text-align: center;
  margin-top: 128px;
  color: chocolate;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
}
</style>
