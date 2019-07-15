<template>
  <div class="filters">
    <FilterCard v-on:click.native="filterResults('All')" label="All"
      imgUrl="https://raw.githubusercontent.com/varunsob/go-explore/master/src/assets/all.png" />
    <FilterCard v-on:click.native="filterResults('Parks')" label="Parks"
      imgUrl="https://raw.githubusercontent.com/varunsob/go-explore/master/src/assets/park.png" />
    <FilterCard v-on:click.native="filterResults('Bars')" label="Bars"
      imgUrl="https://raw.githubusercontent.com/varunsob/go-explore/master/src/assets/bar.png" />
    <FilterCard v-on:click.native="filterResults('Cafés')" label="Cafés"
      imgUrl="https://raw.githubusercontent.com/varunsob/go-explore/master/src/assets/cafe.png" />
    <FilterCard v-on:click.native="filterResults('Lounges')" label="Lounges"
      imgUrl="https://raw.githubusercontent.com/varunsob/go-explore/master/src/assets/lounge.png" />
    <FilterCard v-on:click.native="filterResults('Theaters')" label="Theaters"
      imgUrl="https://raw.githubusercontent.com/varunsob/go-explore/master/src/assets/theater.png" />
  </div>
</template>

<script>
import FilterCard from './FilterCard';

export default {
  name: 'FilterLayout',

  components: {
    FilterCard
  },

  props: {
    fetchVenueList: Function,
  },

  methods: {
    filterResults(value) {
      this.fetchVenueList(value);
    }
  }
}
</script>

<style scoped>
.filters {
  overflow-x: scroll;
  overflow-y: hidden;
  white-space: nowrap;
}
</style>
