<template>
  <ul class="alphabet">
    <li
      class="item"
      v-for="item in letters"
      :key="item"
      @touchstart.prevent="touchStart"
      @touchmove="touchMove"
      @touchend="touchEnd"
      @click="handerLetterClick"
      :ref="item"
    >
      {{ item }}
    </li>
  </ul>
</template>
<script>

import BScroll from 'better-scroll'
export default {
  name: "CityList",
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  props: {
    cities: Object
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    handerLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    //手指按下
    touchStart () {
      this.touchStatus = true
    },
    //手指滑动
    touchMove (e) {
      // 使用了节流
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 79
          const index = Math.floor((touchY - this.startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        },16)

      }
    },
    //手指抬起
    touchEnd () {
      this.touchStatus = false
    }
  },
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.alphabet {
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: absolute;
  top: 1.58rem;
  right: 0;
  bottom: 0;
  width: 0.4rem;
  overflow: hidden;

  .item {
    line-height: 0.4rem;
    align-items: center;
    color: $bgColor;
  }
}
</style>
