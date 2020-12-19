<template>
  <div>
    <div class="item" v-for="(item, index) of list" :key="index">
      <div class="item-title">
        <span class="item-title-icon"></span>
        {{ item.title }}
      </div>
      <div v-if="item.children" class="item-children">
        <detail-list :list="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DetailList",
  props: {
    list: Array
  },
  data () {
    return {};
  },
  created () { }
};
</script>

<style lang="stylus" scoped>
.item-title {
  line-height: 0.8rem;
  font-size: 0.32rem;
  padding: 0.2rem;

  .item-title-icon {
    display: inline-block;
    width: 0.6rem;
    height: 0.6rem;
    background: url('http://simg3.qunarzz.com/piao/images/touch/checkbox_l.png');
  }

}
</style>
