<template>
  <div class="page">
    <wv-swipe class="demo-swipe" :height="130" :auto="4000">
      <wv-swipe-item class="demo-swipe-item" style="background-color: #f44336">1</wv-swipe-item>
      <wv-swipe-item class="demo-swipe-item" style="background-color: #ffc107">2</wv-swipe-item>
      <wv-swipe-item class="demo-swipe-item" style="background-color: #03a9f4">3</wv-swipe-item>
    </wv-swipe>

    <wv-swipe class="demo-swipe" :height="130" :auto="0">
      <wv-swipe-item class="demo-swipe-item" style="background-color: #f44336">1</wv-swipe-item>
      <wv-swipe-item class="demo-swipe-item" style="background-color: #ffc107">2</wv-swipe-item>
      <wv-swipe-item class="demo-swipe-item" style="background-color: #03a9f4">3</wv-swipe-item>
    </wv-swipe>

    <wv-swipe class="demo-swipe" :height="130" :show-indicators="false" :auto="5000">
      <wv-swipe-item class="demo-swipe-item" style="background-color: #f44336">单张轮播</wv-swipe-item>
    </wv-swipe>
  </div>
</template>

<script>
export default {
  data () {
    return {
    }
  }
}
</script>

<style scoped lang="scss">
  .demo-swipe {
    margin-bottom: 50px;

    .demo-swipe-item {
      font-size: 1.2rem;
      color: white;
      font-weight: bold;
      text-align: center;
      line-height: 130px;
    }
  }
</style>
