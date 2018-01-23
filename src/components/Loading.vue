<template>
  <div class="loading-wrapper">
    <div class="loading-content">
    <div class="thumbnail" />
    <div class="info">
      <div class="bar"/>
      <div class="bar half"/>
    </div>
  </div>
  </div>
</template>

<style lang="scss" scoped>
* {
  box-sizing: border-box;
}
.loading-wrapper {
  width: 33%;
  float: left;
  padding: 0.5rem;
}
.loading-content {
  border: 1px solid #ddd;
}
.thumbnail {
  display: block;
  height: 0;
  padding: 25%;
  width: 100%;
  animation: shine 1s infinite;
  background: linear-gradient(to right, #ddd, #f2f2f2);
}
.info {
  display: block;
  padding: 2rem;
  .bar {
    animation: shine 1s infinite;
    background: linear-gradient(to right, #ddd, #f2f2f2);
    margin-bottom: 2rem;
    width: 100%;
    height: 2rem;
    &.half {
      width: 50%;
    }
  }
}

@keyframes shine {
  0% {
    opacity: 1;
  }
  50% {
    opacity: .5;
  }
  100% {
    opacity: 1;
  }
}
</style>
