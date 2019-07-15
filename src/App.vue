<template>
  <div id="app">
    <Header />
    <FilterLayout :fetchVenueList="fetchVenueList" />
    <CardLayout v-if="lat && lon" :fetchVenueList="fetchVenueList" :venuesList="venuesList" :totalResults="totalResults" />
    <div v-else class="location-not-available">
      {{ AppConstants.LOCATION_UNAVAILABLE }}
    </div>
  </div>
</template>

<script>
import { AppConstants } from './constants/strings.js'
import { Keys } from './constants/keys.js'
import { URLs } from './constants/urls.js'

import CardLayout from './components/CardLayout';
import FilterLayout from './components/FilterLayout';
import Header from './components/Header';
import Vue from 'vue';

export default {
  name: 'app',
  components: {
    CardLayout,
    FilterLayout,
    Header,
  },

  data() {
    return {
      AppConstants: AppConstants,
      error: '',
      lat: '',
      lon: '',
      venuesList: null,
      totalResults: 0
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
        this.error = AppConstants.GEOLOCATION_NOT_SUPPORTED;
      }
    },
    setPosition: function(position) {
      this.lat = position.coords.latitude;
      this.lon = position.coords.longitude;
    },
    fetchVenueList(filter) {
      let query = "";
      if (filter !== 'All' )
        query = "&query='"+ filter +"'";
      Vue.http.get(URLs.EXPLORE + '?ll=' + this.lat + ',' + this.lon + query + '&client_id=' + Keys.CLIENT_ID + '&client_secret=' + Keys.CLIENT_SECRET + '&v=20190710')
      .then(response => {
          this.totalResults = response.data.response.totalResults;
          this.venuesList = response.data.response.groups[0].items;
      });
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
.location-not-available {
  margin-top: 50px;
  padding-left: 10px;
  padding-right: 10px;
  text-align: center;
}
</style>
