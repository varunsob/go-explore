<template>
  <div class="header">
    <img class="logo" alt="Explore" src="../assets/logo.png">
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    msg: String
  }
}
</script>

<style scoped>
.header {
  background: linear-gradient(45deg, #0ABF53 0%, #4EE5E5 100%);
  height: 50px;
}
.logo {
  margin: 9px 0 0 10px;
  width: 32px;
}
</style>
