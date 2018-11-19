<template>
  <div id="collect">
    <Header></Header>
    <Searcher :logoFont="logoFont"></Searcher>
    <collect-collected :list="list" v-if="cledShow"></collect-collected>
    <collect-empty v-if="!cledShow"></collect-empty>
  </div>
</template>

<script>
import CollectCollected from './components/Collected'
import CollectEmpty from './components/Empty'
import axios from 'axios'
export default {
  name: 'Collect',
  components: {
    CollectCollected,
    CollectEmpty
  },
  data () {
    return {
      list: [],
      logoFont: '收藏中心'
    }
  },
  methods: {
    getColtInfo () {
      axios.get('/api/collect.json')
        .then(this.getColtInfoSucc)
    },
    getColtInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.list = data.collectList
      }
    }
  },
  mounted () {
    this.getColtInfo()
  },
  computed: {
    cledShow () {
      return this.list.length
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../../assets/styles/varible';
#collect /deep/ .logo_font img {
  display: none;
}
#collect /deep/ .logo_text {
  display: block !important;
}
#collect /deep/ .search_img {
  display: none;
}
#collect /deep/ .search_cart {
  float: right;
}
.wrapper {
  width: $width;
  margin: 0 auto;
  background-color: inherit;
}
</style>
