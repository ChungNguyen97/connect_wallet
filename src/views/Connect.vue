<template>
  <div>
    <h3>Connecting....</h3>
  </div>
</template>

<script>
export default {
  name:'ConnectPage',
  async created(){
    await  window?.fewcha?.connect()
  }
}
</script>

<style>

</style>