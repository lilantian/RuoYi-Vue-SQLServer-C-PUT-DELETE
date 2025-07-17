<template>
  <div id="pps">
<!--    <iFrame-->
<!--      :src="url"-->
<!--      class="map-frame"-->
<!--    />-->
  </div>
</template>

<script>

export default {
  name: 'MagicDev',
  data() {
    return {
      url: process.env.VUE_APP_BASE_API + "/magic/web/",
    }
  },

  mounted() {
    // 加载完成后自动跳转
    window.open(this.url);
    // 重定向到首页，同时关闭当前页面
    window.location.href = '/';
  }
}
</script>

<style scoped lang="scss">
#pps {
  height: calc(100vh - 84px);
  width: 100%;
  background: #fff;

  .map-frame {
    height: 100%;
    width: 100%;
    border: 0
  }
}
</style>
