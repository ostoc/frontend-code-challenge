<template>
    <div class="pagenation">
      <button @click="prePage" :class="{disable: disabledButton}">&larr;</button>
       <button @click="nextPage">&rarr;</button>
    </div>
</template>
<script>
export default {
  name: 'Pagenation',
  data() {
    return {
      currentPage: 0,
    };
  },
  computed: {
    disabledButton() {
      return this.currentPage === 0;
    },
  },
  methods: {
    nextPage() {
      this.currentPage += 1;
      this.$emit('pageClicked', this.currentPage);
    },
    prePage() {
      if (this.currentPage !== 0) {
        this.currentPage -= 1;
        this.$emit('pageClicked', this.currentPage);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.pagenation {
  float: right;
  display: block;
  margin: 1.2rem 0;
}
button {
  width: 4rem;
  height: 4rem;
  float: left;
  margin: 0 1.2rem;
  background: #fff;
  border: 1px solid #dbdbdb;
  cursor: pointer;
  &:hover {
    background: #f2f2f2;
  }
  &.disable {
    opacity: 0.5;
    cursor: not-allowed;
    &:hover {
      background: transparent;
    }
  }
}
</style>
