<template>
  <div class="filter-card card-border">
    <img class="card-bg" :src="imgUrl" />
    <p class="label">{{label}}</p>
  </div>
</template>

<script>
export default {
  name: 'FilterCard',
  props: {
    imgUrl: String,
    label: String
  }
}
</script>

<style scoped>
.filter-card {
  width: 75px;
  height: 75px;
  margin: 12px;
  display: inline-block;
}
.card-border {
  border: 1px solid #fff;
  border-radius: 50%;
}
.card-bg {
  border-radius: 50%;
  height: 75px;
  width: 75px;
}
.label {
  width: 100%;
  text-align: center;
  color: #000;
  font-size: 14px;
  font-weight: 500;
}
</style>
