<template>
  <div id="header">
    <div class="wrapper">
      <p class="h_left">
        <a href="">云蚂蚁官网</a>Hi,<a href="" class="active">{{this.user['name']}}</a><a href="">退出</a>
      </p>

      <div class="h_right">
        <ul>
          <li><a href="">批发首页</a></li>
          <li><a href="">会员中心</a></li>
          <li><a href="">当面付申请</a></li>
          <li><a href="">快递代收</a></li>
          <li><a href="">进货单</a></li>
          <li><a href="">收藏夹</a></li>
          <li><a href="">帮助中心</a></li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Header',
  data () {
    return {
      user: {
        'id': '100673',
        'name': 'maijia'
      }
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/home.json')
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.user = data.user
      }
    }
  },
  mounted () {
    this.getHomeInfo()
  }
}
</script>

<style lang="scss" scoped>
  @import '~@/assets/styles/varible.scss';
  #header {
    height: 30px;
    font-size: 12px;
    text-align: center;
    line-height: 30px;
    background-color: $bgColor1;
    @extend %wrapper;
    .h_left {
      float: left;
      padding-left: 0;
      color: rgba(102,102,102,1);
      a {
        color: rgba(102,102,102,1);
        padding-right: 20px;
      }
      a.active {
        color: rgba(230,45,45,1);
        text-indent: 4px;
        display: inline-block;
      }
    }
    .h_right {
      float: right;
      padding-right: 0;

      li {
        display: inline-block;
        float: left;
        padding-left: 20px;
        a {
          color: rgba(102,102,102,1);
        }
      }
    }
  }

</style>
