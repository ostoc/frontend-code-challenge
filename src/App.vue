<template>
  <div id="app">
    <Listing v-for="item in pagedData" :key="item.id"
    :title="item.title"
    :purpose="item.purpose"
    :thumbnail="item.advertisementAssets"
    :postalCode="item.realestateSummary.address.postalCode"
    :city="item.realestateSummary.address.city"
    :price="item.advertisementPrice.sellPrice"
    :numberOfRooms="item.realestateSummary.numberOfRooms"
    :space="item.realestateSummary.space"/>
    <pagenation v-on:pageClicked="updatePage"/>
  </div>
</template>

<script>
import Listing from './components/ListingTemplate';
import Pagenation from './components/Pagenation';

export default {
  name: 'App',
  components: {
    Listing, Pagenation,
  },
  mounted() {
    const BASEURL = 'api/advertisements';
    this.$http.get(BASEURL, {}).then((response) => {
      this.advertisementData = response.data.data;
    });
  },
  data() {
    return {
      advertisementData: '',
      pageNumber: 0,
    };
  },
  computed: {
    pagedData() {
      const startItem = this.pageNumber * 6;
      const endItem = (this.pageNumber + 1) * 6;
      return this.advertisementData.slice(startItem, endItem);
    },
  },
  methods: {
    updatePage(value) {
      this.pageNumber = value;
      window.scrollTo(0, 0);
    },
  },
};
</script>
