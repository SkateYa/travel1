<template>
  <div class="list" ref="wrapper">
    <div class="content">
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{ this.$store.state.city }}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div
            class="button-wrapper"
            v-for="(item, key) in hotCities"
            :key="key"
            @click="handelCityClick(item.name)"
          >
            <div class="button">{{ item.name }}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item, key) in cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{ key }}</div>
        <div class="item-list" v-for="innerItem in item" :key="innerItem.id">
          <div
            class="item border-bottom"
            @click="handelCityClick(innerItem.name)"
          >
            {{ innerItem.name }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>

import BScroll from 'better-scroll'
export default {
  name: "CityList",
  props: {
    cities: Object,
    hotCities: Array,
    letter: String
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        //如果滑动不了就重新写一次
         this.scroll.scrollToElement(element)
        // this.scroll.scrollToElement(element)
      }
      console.log(this.letter)
    }
  },
  mounted () {
    this.$nextTick(() => {
      if (!this.scroll) {
        this.scroll = new BScroll(this.$refs.wrapper)
        console.log(this.scroll)
      }
    })
  },
  methods: {
    handelCityClick (city) {
      this.$store.dispatch('changeCity', city)
      this.$router.push('/')
    }
  },
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.border-topbottom {
  &:before {
    border-color: #ccc;
  }

  &:after {
    border-color: #ccc;
  }
}

.border-bottom {
  &:before {
    border-color: #ccc;
  }
}

/* 设置滚动区域 */
.list {
  position: absolute;
  top: 1.78rem;
  left: 0;
  right: 0;
  bottom: 0;
  overflow: hidden;
  touch-action: none;
}

.title {
  line-height: 0.44rem;
  background: #ccc;
  padding-left: 0.2rem;
  color: #666;
  font-size: 0.26rem;
}

.button-list {
  padding: 0.1rem 0.6rem 0.1rem 0.1rem;
  overflow: hidden;

  .button-wrapper {
    float: left;
    width: 33.33%;

    .button {
      text-align: center;
      margin: 0.1rem;
      padding: 0.1rem 0;
      border: 0.02rem solid #ccc;
      border-radius: 0.06rem;
    }
  }
}

.item-list {
  .item {
    line-height: 0.76rem;
    color: #666;
    padding-left: 0.2rem;
  }
}
</style>
