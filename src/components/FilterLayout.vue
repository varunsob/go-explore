<template>
  <div class="filters">
    <FilterCard v-on:click.native="filterResults('All')" label="All"
      imgUrl="https://fastly.4sqi.net/img/general/original/13764780_Ao02DfJpgG1ar2PfgP51hOKWsn38iai8bsSpzKd0GcM.jpg" />
    <FilterCard v-on:click.native="filterResults('Parks')" label="Parks"
      imgUrl="https://fastly.4sqi.net/img/general/original/13764780_Ao02DfJpgG1ar2PfgP51hOKWsn38iai8bsSpzKd0GcM.jpg" />
    <FilterCard v-on:click.native="filterResults('Bars')" label="Bars"
      imgUrl="https://fastly.4sqi.net/img/general/original/5117421_g7AiNcpw8eBO9r8plGQnwaWCkSTyzMADt16kDLnWSpk.jpg" />
    <FilterCard v-on:click.native="filterResults('Cafés')" label="Cafés"
      imgUrl="https://fastly.4sqi.net/img/general/original/17460311_KyENmUYgz4uFrZqU3QppGJsq85mCckBnX_qIV11C8LM.jpg" />
    <FilterCard v-on:click.native="filterResults('Lounges')" label="Lounges"
      imgUrl="https://fastly.4sqi.net/img/general/original/150415926_m_tyDKcI1B_dbDKtJMKbV_TzcAhJimN1r4sAI7cqSKs.jpg" />
    <FilterCard v-on:click.native="filterResults('Theaters')" label="Theaters"
      imgUrl="https://fastly.4sqi.net/img/general/original/150415926_m_tyDKcI1B_dbDKtJMKbV_TzcAhJimN1r4sAI7cqSKs.jpg" />
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
