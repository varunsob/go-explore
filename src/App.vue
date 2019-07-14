<template>
  <div id="app">
    <Header />
    <FilterLayout />
    <CardLayout v-if="lat && lon" :lat="lat" :lon="lon" />
  </div>
</template>

<script>
import CardLayout from './components/CardLayout';
import FilterLayout from './components/FilterLayout';
import Header from './components/Header';

export default {
  name: 'app',
  components: {
    CardLayout,
    FilterLayout,
    Header,
  },

  data() {
    return {
      error: '',
      lat:'',
      lon:''
    }
  },

  created() {
    this.getLocation();
  },

  methods: {
    getLocation: function () {
      if(navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(this.setPosition);
      } else {
        this.error = "Geolocation is not supported.";
      }
    },
    setPosition: function(position) {
      this.lat = position.coords.latitude;
      this.lon = position.coords.longitude;
    }
	}
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#app {
  font-family: "Fakt",sans-serif,Helvetica,Arial;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.segment-title {
  color: #000;
  font-size: 24px;
  font-weight: 600;
  margin: 20px;
  text-align: left;
}
</style>
