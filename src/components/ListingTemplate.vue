<template>
  <div class="Listing">
    <div class="" v-text="status">ff d</div>
    <div class="">
      <img :src="thumbnail">
    </div>
    <div class="" v-text="title"></div>
    <div class="" v-text="postalCode"></div>
    <div class="" v-text="city"></div>
    <div class="" v-text="price"></div>
    <div class="" v-text="numberOfRooms"></div>
    <div class="" v-text="space"></div>
  </div>
</template>

<script>
export default {
  name: 'Listing',
  props: {
    thumbnail: String,
    status: 'Mieten',
    title: String,
    postalCode: String,
    price: Number,
    city: String,
    numberOfRooms: Number,
    space: Number,
  },
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
