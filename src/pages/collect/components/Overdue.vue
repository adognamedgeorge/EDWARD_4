<template>
  <div>
    <section class="section2">
      <ul>
        <li class="item_box" v-for="item of list" :key="item.id" v-if="!item.isCollect">
          <div class="item_img">
            <a href="" target="_blank"><img :src="item.img"/></a>
          </div>
          <div class="item_title">
            <a href="" target="_blank">{{item.title}}</a>
          </div>
          <div class="item_price">
            <i>￥</i><strong>{{item.price}}</strong>/{{item.unit}}
            <span>规格:{{item.spec}}</span>
          </div>
          <div class="item_action" v-if="item.isCollect">
            <a href="javascript:;">-</a>
            <input type="text" :value="item.minSoldNum" data-min="1"/>
            <a href="javascript:;">+</a>
            <a href="javascript:;">进货</a>
          </div>
          <!--失效商品-->
          <div class="item_overdue iconfont clearfix" v-if="!item.isCollect">
            <i>&#xe602;</i>
            <span>此宝贝已失效</span>
          </div>
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
export default {
  name: 'CollectOverdue',
  // props: {
  //   list: Array
  // },
  data () {
    return {
      list: [
        {
          'id': '110974',
          'stock': '100',
          'img': 'http://pifa.yunmayi.com/upload/2015/10/21/165dfcb4125eec29a429f10ce8e45e5c.jpg',
          'title': '1111111111111',
          'spec': '10kg/袋',
          'unit': '袋',
          'price': '105.50',
          'minSoldNum': '3',
          'isCollect': 1
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
        }, {
          'id': '110978',
          'stock': '110',
          'img': '/upload/eba1c2ef98775bf4431d2ebd472eab51.jpg',
          'title': '55555555',
          'spec': '90kg/袋',
          'unit': '袋',
          'price': '905.50',
          'minSoldNum': '5',
          'isCollect': 0
        }, {
          'id': '110979',
          'stock': '110',
          'img': '/upload/eba1c2ef98775bf4431d2ebd472eab51.jpg',
          'title': '55555555',
          'spec': '90kg/袋',
          'unit': '袋',
          'price': '905.50',
          'minSoldNum': '5',
          'isCollect': 1
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '~@/assets/styles/varible.scss';
  .section2 {
    padding-top: 20px;
    box-shadow: 0 -1px 0 0 rgba(242, 242, 242, 1);
    ul {
      margin-bottom: 10px;
      display: inline-block;
      @extend %item;
      .item_box {
        margin-bottom: 10px;
        margin-left: 10px;
        border: 1px solid rgba(242, 242, 242, 1);
        width: 228px;
        .item_overdue {
          text-align: center;
          color: rgba(51, 51, 51, 1);
          font-size: 16px;
          height: 26px;
          line-height: 26px;
          i {
            font-size: 24px;
            color: rgba(216, 216, 216, 1);
            display: inline-block;
            vertical-align: middle;
            margin-top: -2px;
          }
        }
      }
      .item_box:nth-child(5n+1) {
        margin-left: 0;
      }
      .item_box:hover {
        transform: unset;
        box-shadow: unset;
      }
    }
  }
</style>
