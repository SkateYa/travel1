<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img
        class="banner-image"
        src="http://img1.qunarzz.com/sight/source/1510/6e/1ea71e2f04e.jpg_r_640x214_aa6f091d.jpg"
        alt=""
      />
      <div class="banner-info">
        <div class="banner-title">大连圣亚海洋世界（AAAA景区）</div>
        <div class="banner-number">
          <span class="iconfont">&#xe632;</span>39
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallary
        @close="handleGallaryClose"
        :imgs="imgs"
        v-show="showGallary"
      ></common-gallary>
    </fade-animation>
  </div>
</template>

<script>
// import CommonGallary from "common/gallary/Gallay"
import CommonGallary from "../../../common/gallary/Gallary"
import FadeAnimation from "../../../common/fade/Fade"
export default {
  name: 'DetailBanner',
  components: {
    CommonGallary,
    FadeAnimation
  },
  data () {
    return {
      showGallary: false,
      imgs: ['https://imgs.qunarzz.com/vs_ceph_vs_tts/fafe9394-8e5f-4ca9-b284-0cde9e516723.jpg_r_390x260x95_de847494.jpg',
        'https://imgs.qunarzz.com/vs_ceph_vs_tts/5de1eefc-8587-4714-89f0-c61acb3faf77.jpg_r_390x260x95_4af2fb70.jpg']
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleGallaryClose () {
      this.showGallary = false
    }
  },
}
</script>
<style lang="stylus" scoped>
.banner {
  position: relative;
  overflow: hidden;
  height: 0;
  padding-bottom: 55%;

  .banner-image {
    width: 100%;
  }

  .banner-info {
    display: flex;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    top: 2.43rem;
    line-height: 0.3rem;
    color: #fff;

    .banner-title {
      flex: 1;
    }

    .banner-number {
      padding: 0.1rem;
      height: 0.2rem;
      line-height: 0.2rem;
      border-radius: 0.2rem;
      background: rgba(0, 0, 0, 0.8);
    }
  }
}
</style>
