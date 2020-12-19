<template>
  <div class="container" @click="handleGallaryClick">
    <div class="wrapper">
      <swiper :options="swiperOption">
        <swiper-slide v-for="(item, index) in imgs" :key="index">
          <img class="gallary-img" :src="item" />
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>


<script>
export default {
  name: 'CommenGallay',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
       paginationClickable :true,
        observeParents:true,
        observer:true,
      },

    }
  },
  methods: {
    handleGallaryClick(){
      this.$emit('close')
    }
  },
  mounted () {
    console.log('imgs==========', this.imgs)
  }
}
</script>


<style lang="stylus" scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  z-index: 99;
  position: fixed;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  background-color: red;

  .wrapper {
    width: 100%;
    height: 0;
    overflow: hidden;
    padding-bottom: 100%;

    .gallary-img {
      width: 100%;

      .swiper-pagination {
        color: #fff;
      }
    }
  }
}
</style>
