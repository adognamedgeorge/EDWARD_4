<template>
  <div id="ca_main" class="wrapper">
    <div class="sm_recorder">
      <a href="">默认</a>
      <a href="">销量<i class="re_bg1"> </i></a>
      <a href="">价格<i class="re_bg2"> </i></a>
      <div>
        共<span>{{this.sList.length}}</span>个商品
      </div>
    </div>

    <div class="search_item_box">
      <ul>
        <li class="item_box" v-for="item of sList" :key="item.id">
          <a class="item_bg"> </a>
          <div class="item_img">
            <a href="" target="_blank">
              <img :src="item.img"/>
            </a>
          </div>
          <div class="item_title">
            <a href="" target="_blank">{{item.title}}</a>
          </div>
          <div class="item_price">
            <i>￥</i><strong>{{item.price}}</strong>/{{item.unit}}
            <span>规格:{{item.spec}}</span>
          </div>
          <div class="item_action">
            <a href="javascript:;">-</a>
            <input type="text" :value="item.minSoldNum" data-min="1"/>
            <a href="javascript:;">+</a>
            <a href="">进货</a>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchCategory',
  // props: {
  //   sList: Array
  // }
  data () {
    return {
      sList: [
        {
          'id': '110974',
          'stock': '100',
          'img': 'http://pifa.yunmayi.com/upload/2015/10/21/165dfcb4125eec29a429f10ce8e45e5c.jpg',
          'title': '1111111111111',
          'spec': '10kg/袋',
          'unit': '袋',
          'price': '105.50',
          'minSoldNum': '3',
          'isCollect': 0
        }, {
          'id': '110975',
          'stock': '900',
          'img': 'http://pifa.yunmayi.com/upload/2015/10/21/165dfcb4125eec29a429f10ce8e45e5c.jpg',
          'title': '2222222222222222222',
          'spec': '310kg/袋',
          'unit': '箱',
          'price': '15.50',
          'minSoldNum': '4',
          'isCollect': 1
        }, {
          'id': '110976',
          'stock': '110',
          'img': '/upload/eba1c2ef98775bf4431d2ebd472eab51.jpg',
          'title': '333333333333333',
          'spec': '90kg/袋',
          'unit': '袋',
          'price': '905.50',
          'minSoldNum': '5',
          'isCollect': 0
        }, {
          'id': '110977',
          'stock': '110',
          'img': 'http://pifa.yunmayi.com/upload/2015/10/21/165dfcb4125eec29a429f10ce8e45e5c.jpg',
          'title': '44444444444444444444',
          'spec': '90kg/袋',
          'unit': '袋',
          'price': '905.50',
          'minSoldNum': '6',
          'isCollect': 1
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '~@/assets/styles/varible.scss';
  #ca_main {
    //background-color:$bgColor2;
    padding-top: 30px;
    padding-bottom: 30px;
    //@extend %wrapper;
    .sm_recorder {
      height: 26px;
      background-color: rgba(245,245,245,1);
      margin-bottom: 20px;
      padding: 7px 10px;
      a {
        float: left;
        font-size: 14px;
        color: rgba(153,153,153,1);
        display: inline-block;
        width: 70px;
        height: 26px;
        background: $color;
        text-align: center;
        line-height: 26px;
        border: 1px solid rgba(230,230,230,1);
        i {
          display: inline-block;
          width: 16px;
          height: 18px;
          vertical-align: middle;
          background: $Sprite;
        }
        .re_bg1 { background-position: -456px 0; }
        .re_bg2 { background-position: -473px 0; }
      }
      a:first-child { width: 60px; }

      div {
        float: right;
        border: 1px solid rgba(230,230,230,1);
        background-color: $color;
        min-width: 82px;
        padding: 0 9px;
        height: 26px;
        font-size: 14px;
        line-height: 26px;
        color: rgba(153,153,153,1);
        text-align: center;
      }
    }

    .search_item_box {
      ul {
        display: inline-block;
        margin-bottom: 10px;
        @extend %item;
        .item_box {
          margin-bottom: 10px;
          margin-left: 10px;
        }
        .item_box:nth-child(5n+1) {
          margin-left: 0;
        }
      }
    }
  }
</style>
