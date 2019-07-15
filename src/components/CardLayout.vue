<template>
  <div class="venues">
    <div class="segment-title">
      <p>{{ CardLayoutConstants.POPULAR }} <span class="total-count">{{ this.totalResults? this.totalResults: "---" }} options available</span></p>
    </div>
    <Card v-for="venue in this.venuesList" v-bind:key="venue.id" :venue="venue" />
  </div>
</template>

<script>
import { CardLayoutConstants } from '../constants/strings.js'

import Card from './Card';

export default {
  name: 'CardLayout',

  props: {
    fetchVenueList: Function,
    venuesList: Array,
    totalResults: Number
  },

  components: {
    Card
  },

  data() {
    return {
      CardLayoutConstants: CardLayoutConstants
    }
  },

  created() {
    this.fetchVenueList("all");
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
