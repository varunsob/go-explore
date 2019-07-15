<template>
  <div class="header">
    <img class="logo" alt="Explore" src="../assets/logo.png">
    <div class="title">Go Explore</div>
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
  float: left;
  margin: 9px 0 0 10px;
  width: 32px;
}
.title {
  color: #fff;
  float: left;
  font-size: 18px;
  margin: 15px 0 0 15px;
  top: 0;
}
</style>
