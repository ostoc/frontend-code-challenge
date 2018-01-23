<template>
  <div id="app">
    <Listing v-for="item in pagedData" :key="item.id" 
    :title="item.title"
    :thumbnail="item.advertisementAssets[0].advertisementThumbnails.inventory_m.url"
    :postalCode="item.realestateSummary.address.postalCode"
    :city="item.realestateSummary.address.city"
    :price="item.advertisementPrice.sellPrice"
    :numberOfRooms="item.realestateSummary.numberOfRooms"
    :space="item.realestateSummary.space"/>
  </div>
</template>

<script>
/* eslint-disable */
import Listing from './components/ListingTemplate';

export default {
  name: 'App',
  components: {
    Listing,
  },
  mounted() {
    const BASEURL = 'api/advertisements';
    this.$http.get(BASEURL, {
    }).then((response) => {
      this.advertisementData = response.data.data;
    });
  },
  data() {
    return {
      advertisementData: '',
      pageNumber: 0,
    }
  },
  computed: {
    pagedData() {
      let startItem = this.pageNumber * 9;
      let endItem = (this.pageNumber + 1) * 9;
      return this.advertisementData.slice(startItem, endItem);
    }
  }

};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
