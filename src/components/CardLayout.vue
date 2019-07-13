<template>
  <div class="venues">
    <div class="segment-title">
      <p>Popular near you <span class="total-count">{{totalResults? totalResults: "---"}} options available</span></p>
    </div>
    <Card v-for="venue in venuesList" v-bind:key="venue.id" :venue="venue" />
  </div>
</template>

<script>
import Card from './Card';
import Vue from 'vue';
import VueResource from 'vue-resource';
Vue.use(VueResource);

export default {
  name: 'CardLayout',

  props: {
    lat: Number,
    lon: Number
  },

  components: {
    Card
  },

  data() {
    return {
      venuesList: null,
      totalResults: 0,
    }
  },

  created() {
    this.fetchVenues();
  },

  methods: {
    fetchVenues() {
      Vue.http.get('https://api.foursquare.com/v2/venues/explore?ll='+this.lat+','+this.lon+'&client_id=Z1HSHTJQLY4XT3YXGXJJNPWUFPJHPZDUJAE3LMFKXUPS0UJ3&client_secret=LYSNFZR5UBCE433BFKAHQXULOHRQYP1LEYQWBX5QHF5235ED&v=20190710')
      .then(response => {
          this.totalResults = response.data.response.totalResults;
          this.venuesList = response.data.response.groups[0].items;
      });
    }
  }
}
</script>

<style scoped>
.venues {
  margin: 0 auto;
  text-align: center;
  width: 100%;
}
.total-count {
  font-size: 11px;
  font-weight: 400;
}
</style>
