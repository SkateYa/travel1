<template>
  <div>
    <detail-banner></detail-banner>
    <detail-list :list="list"></detail-list>
  </div>
</template>

<script>
import DetailBanner from './components/banner'
import DetailList from './components/list'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailList
  },
  data () {
    return {
      list: [
        { title: '成人票', children: [{ title: '成人二级联票' ,children: [{ title: '成人二级联票-zzz' }]}, { title: '成人三级联票' }] }, { title: '学生票' }, { title: '儿童票' }, { title: '特惠票' }
      ]
    }
  },
  created () {
  },

}
</script>

<style lang="stylus" scoped></style>
