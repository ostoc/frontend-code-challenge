<template>
  <div class="listing-wapper">
    <div class="listing">
    <div class="listing--thumbnail">
      <img :src="thumbnailUrl">
    </div>
    <div class="listing--summary">
      <div class="purpose" v-text="purpose ? 'Kaufen' : 'Mieten'" />
      <div class="title" v-text="title" />
      <div class="address" v-text="address"/>
      <div class="info">
        <div class="price"
        v-text="displayPrice"/>
        <div class="addition-info">
        <span class="rooms">
          {{numberOfRooms}} Zimmer
        </span>
        <span class="space">
          ab {{space.toFixed(2)}} m&#178;
        </span>
        </div>

      </div>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Listing',
  props: {
    thumbnail: Object,
    purpose: Number,
    title: String,
    postalCode: String,
    price: Number,
    city: String,
    numberOfRooms: Number,
    space: Number,
  },
  computed: {
    address() {
      return `${this.postalCode} / ${this.city}`;
    },
    thumbnailUrl() {
      if (this.thumbnail[0]) {
        return this.thumbnail[0].advertisementThumbnails.inventory_m.url;
      }
      return this.thumbnail.advertisementThumbnails.inventory_m.url;
    },
    displayPrice() {
      if (this.price) {
        return this.price.toLocaleString('de-DE', { style: 'currency', currency: 'EUR' });
      }
      return 'N/A';
    },
  },
};
</script>

<style lang="scss" scoped>
* {
  font-family: 'Gill Sans', Calibri, 'Trebuchet MS', sans-serif;
  box-sizing: border-box;
}
.listing-wapper {
  width: 33%;
  float: left;
  padding: .5rem;
}
.listing {
  border: 1px solid #dbdbdd;
  position: relative;
}
.listing--thumbnail {
  img {
    width: 100%;
    height: 100%;
  }
}

.listing--summary {
  padding: 2rem;
  .purpose {
    background: #fff;
    position: absolute;
    left: 1rem;
    top: 1rem;
    color: #b1b1b1;
    padding: .5rem;
    border-radius: 2px;
    box-shadow: 0 2px 2px rgba(0, 0, 0, .3);
  }
  .title {
    hyphens: auto;
    font-size: 1.1em;
    line-height: 1.2em;
    white-space: word;
    height: 2.4em;
    overflow: hidden;
    color: #333;
    margin-bottom: .5rem;
  }
  .address {
    line-height: 2em;
    font-size: .9em;
    margin-bottom: 1.2rem;
    color: #b1b1b1;
  }

  .info {
    height: 2em;
    width: 100%;
    line-height: 2em;
  }
  .addition-info {
    float: right;
  }
  .price {
    width: 40%;
    font-weight: 600;
    float: left;
  }
  .rooms, .space {
    display: inline-block;
    padding-left: .4em;
    color: #6a6a6a;
    text-align: right;
  }
  .rooms {
    padding-right: .4em;
  }
  .space {
    border-left: 1px solid #dbdbdb;
  }
}

@media (max-width: 374px) {
  .listing-wapper {
    width: 100%;
    padding: .5rem;
  }
  .listing--summary {
    padding: 1rem;
    .info {
      height: 4em;
    }
    .addition-info {
      float: left;
    }
  }
}
@media (min-width: 375px) and (max-width:767px) {
  .listing-wapper {
    width: 100%;
    padding: .5rem;
  }
  .listing--summary {
    padding: 1rem;
  }
}
@media (min-width: 768px) and (max-width: 1200px){
  .listing-wapper {
    width: 50%;
  }
}
</style>
