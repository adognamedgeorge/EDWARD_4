<template>
  <div class="notice" ref="divHeight">
    <ul>
      <li v-for="item of web" :key="item.id">
        <a :href="item.link" @click="iframeShow" target="showHere">{{item.name}}</a>
      </li>
    </ul>
    <iframe id="show_iframe" v-show="iframeState" name="showHere" frameborder="0" scrolling="auto"></iframe>
  </div>
</template>

<script>
export default {
  name: 'AnnounceNotice',
  // props: {
  //   web: Array
  // },
  data () {
    return {
      iframeState: false,
      web: [
        {
          'link': 'http://pifa.yunmayi.com//notice/detail?id=1390',
          'id': 1001,
          'name': '通知1'
        }, {
          'link': 'http://pifa.yunmayi.com//notice/detail?id=1380',
          'id': 1002,
          'name': '通知2'
        }
      ]
    }
  },
  mounted () {
    const oIframe = document.getElementById('show_iframe')
    const divH = this.$refs.divHeight.offsetHeight
    const deviceWidth = document.documentElement.clientWidth
    const deviceHeight = document.documentElement.clientHeight
    oIframe.style.width = deviceWidth + 'px'
    oIframe.style.minHeight = divH + 'px'
  },
  methods: {
    iframeShow () {
      this.iframeState = true
    }
  }
}
</script>

<style lang="scss" scoped>
  .notice {
    flex: 1;
  }
</style>
