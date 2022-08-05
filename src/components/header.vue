<template>
  <header class="header">
    <p v-if="!isConnect" @click="handleConnect">Connect to Fewcha Walle</p>
    <div v-else class="option">
      <p @click="hanldeDisConnect">Disconnect</p>
      <p>
        Balance
        <span class="balance"> ({{ balance }}) </span>
      </p>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComp",
  data: () => ({
    isConnect: "false",
    balance: "",
  }),
  methods: {
    async handleConnect() {
      console.log("connecting.....");
      const r = await window?.fewcha?.connect();
      // console.log("r: ", r);
      if (r.status === 200) {
        this.isConnect = true;
        const balance_value = await window?.fewcha?.getBalance();
        console.log("b_v:", balance_value);
        if (balance_value.data && typeof balance_value.data === "string") {
          this.balance = balance_value.data;
        }
      }
    },
    async hanldeDisConnect() {
      console.log("disconnect.....");
      await window?.fewcha?.disconnect();
      const isConnected = await window?.fewcha?.isConnected();
      console.log("isConnected2: ", isConnected);
      this.isConnect = await isConnected?.data;
    },
  },
  async created() {
    const isConnected3 = await window?.fewcha?.isConnected();
    console.log("isConnected3", isConnected3);
    this.isConnect = await isConnected3?.data;

    const balance_start = await window?.fewcha?.getBalance();
    console.log("balance_start", balance_start);
    if (balance_start?.data && typeof balance_start?.data === "string") {
      this.balance = balance_start.data;
    }
  },
};
</script>

<style lang="scss" scoped>
.header {
  width: 100%;
  background-color: #f5f5f5;
  display: flex;
  justify-content: center;
  gap: 24px;
  font-family: Arial, Helvetica, sans-serif;
  p {
    text-decoration: underline;
    font-weight: 700;
    font-size: 24px;
    line-height: 120%;
    color: blue;
    &:hover {
      cursor: pointer;
      color: red;
    }
  }
}
.option {
  display: flex;
  column-gap: 24px;
}
nav {
  display: flex;
  justify-content: center;
  gap: 24px;
  a {
    color: #333;
    font-weight: 700;
    font-size: 20px;
    line-height: 120%;
    text-decoration: none;
    font-weight: bold;
    color: #2c3e50;
    padding: 7px 12px;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>