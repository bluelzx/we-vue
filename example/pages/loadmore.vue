<template>
	<div class="page">
    <wv-loadmore></wv-loadmore>
    <wv-loadmore type="line" text="loading"></wv-loadmore>
    <wv-loadmore type="lineDot" text="loading"></wv-loadmore>
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
  .page {
    background-color: white;
  }
</style>
