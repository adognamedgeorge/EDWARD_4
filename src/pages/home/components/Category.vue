<template>
  <div class="categories" ref="box"> <!--ref注册引用信息-->
    <div class="wrapper" ref="wrapper">
        <div :id="'c_' + index1" class="category" v-for="(item,index1) of categories" :key="item.id">
          <div class="c_left">
            <div class="left_t">
              <div class="ca_title">
                <a href=""><span>{{item.sideTitle}}</span><i class="i_bg"> </i></a>
              </div>
              <div class="ca_list">
                <ul>
                  <li v-for="item2 of item.sideSorts" :key="item2.id"><a href="">{{item2.name}}</a></li>
                </ul>
              </div>
            </div>
            <div class="left_b">
              <img :src="item.sideImg"/>
            </div>
          </div>

          <div class="c_right">
            <ul>
              <li class="item_box" v-for="(item3, index) of item['categoryList']" :key="item3.id">
                <a class="item_bg"> </a>
                <a class="item_bg cover" v-if="item3.isCollect"> </a>
                <div class="item_img">
                  <a href="" target="_blank"><img :src="item3.img" /></a>
                </div>
                <div class="item_title">
                  <a href="" target="_blank">{{item3.title}}</a>
                </div>
                <div class="item_price">
                  <i>￥</i><strong>{{item3.price}}</strong>/{{item3.unit}}
                  <span>规格:{{item3.spec}}</span>
                </div>
                <div class="item_action" >
                  <a href="javascript:;" @click="reduce(index1,index)" >-</a>
                  <input type="text" :value="parseInt(item3.minSoldNum)" ref="item_count" readonly/>
                  <a href="javascript:;" @click="plus(index)" >+</a>
                  <a style="cursor:pointer;" @click="add(index1,index)">进货</a>
                </div>
              </li>
            </ul>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
// 定义个公共实例文件link.js，作为中间仓库来传值(非父子组件之间)
import Link from '../../public/public_js/link.js'
export default {
  name: 'HomeCategory',
  data () {
    return {
      list: [],
      sorts: {},
      categories: [
        {
          'id': 1001,
          'sideTitle': '酒饮料',
          'sideSorts': [
            {'name': '啤酒', 'id': 1001},
            {'name': '白酒', 'id': 1002}
          ],
          'sideImg': '/static/img/home_banner_L1@2x.png',
          'categoryList': [
            {
              'id': '1001',
              'stock': '100',
              'img': 'http://i8.yunmayi.com/upload/2015/04/30/7b948795d28a540658f4fc6f6da26950.jpgXXXXX!!!!!_300x300.jpg',
              'title': '1111111111五常昌旺纯真100%稻花香',
              'spec': '10kg/袋',
              'unit': '袋',
              'price': '105.50',
              'minSoldNum': '3',
              'isCollect': 0
            },
            {
              'id': '1002',
              'stock': '900',
              'img': 'http://pifa.yunmayi.com/upload/2015/10/21/165dfcb4125eec29a429f10ce8e45e5c.jpg',
              'title': '2五常昌旺纯真100%稻花香',
              'spec': '310kg/袋',
              'unit': '箱',
              'price': '15.50',
              'minSoldNum': '4',
              'isCollect': 1
            },
            {
              'id': '1003',
              'stock': '110',
              'img': 'http://i8.yunmayi.com/upload/2015/04/30/7b948795d28a540658f4fc6f6da26950.jpgXXXXX!!!!!_200x200.jpg',
              'title': '3五常昌旺纯真100%稻花香',
              'spec': '90kg/袋',
              'unit': '袋',
              'price': '905.50',
              'minSoldNum': '5',
              'isCollect': 0
            },
            {
              'id': '1004',
              'stock': '110',
              'img': '/upload/eba1c2ef98775bf4431d2ebd472eab51.jpg',
              'title': '55555五常昌旺纯真100%稻花香',
              'spec': '90kg/袋',
              'unit': '袋',
              'price': '905.50',
              'minSoldNum': '6',
              'isCollect': 1
            },
            {
              'id': '1005',
              'stock': '110',
              'img': '/upload/eba1c2ef98775bf4431d2ebd472eab51.jpg',
              'title': '44455五常昌旺纯真100%稻花香',
              'spec': '330ml*24瓶',
              'unit': '袋',
              'price': '905.50',
              'minSoldNum': '7',
              'isCollect': 1
            }
          ]
        },
        {
          'id': 1002,
          'sideTitle': '儿童玩具',
          'sideSorts': [
            {'name': '气球', 'id': 1003},
            {'name': '皮球', 'id': 1004}
          ],
          'sideImg': '/static/img/home_banner_L1@2x.png',
          'categoryList': [
            {
              'id': '1001',
              'stock': '100',
              'img': 'http://pifa.yunmayi.com/upload/2015/10/21/165dfcb4125eec29a429f10ce8e45e5c.jpg',
              'title': '444五常昌旺纯真100%稻花香',
              'spec': '10kg/袋',
              'unit': '袋',
              'price': '15.50',
              'minSoldNum': '3',
              'isCollect': 1
            }
          ]
        },
        {
          'id': 1003,
          'sideTitle': '日用洗护',
          'sideSorts': [
            {'name': '牙膏', 'id': 1005},
            {'name': '牙刷', 'id': 1006}
          ],
          'sideImg': '/static/img/home_banner_L1@2x.png',
          'categoryList': [
            {
              'id': '1001',
              'stock': '100',
              'img': 'http://i8.yunmayi.com/upload/2015/04/30/7b948795d28a540658f4fc6f6da26950.jpgXXXXX!!!!!_300x300.jpg',
              'title': '222五常昌旺纯真100%稻花香',
              'spec': '10kg/袋',
              'unit': '袋',
              'price': '15.50',
              'minSoldNum': '3',
              'isCollect': 1
            }, {
              'id': '1002',
              'stock': '100',
              'img': 'http://pifa.yunmayi.com/upload/2015/10/21/165dfcb4125eec29a429f10ce8e45e5c.jpg',
              'title': '333五常昌旺纯真100%稻花香',
              'spec': '10kg/袋',
              'unit': '袋',
              'price': '15.50',
              'minSoldNum': '3',
              'isCollect': 1
            }
          ]
        }
      ]
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
        this.categories = data.categories
        this.cartNum = data.cartNum
      }
    },
    plus (index) {
      this.$refs.item_count[index].value++
    },
    reduce (index1, index) {
      if (this.$refs.item_count[index].value <= this.categories[index1]['categoryList'][index].minSoldNum) return
      this.$refs.item_count[index].value--
    },
    add (index1, index) {
      // Link.$emit('val', parseInt(this.list[index].minSoldNum) + parseInt(this.list[index].num))
      const catList = this.categories[index1]['categoryList'][index]
      // 点击进货传值给进货单
      Link.$emit('val',
        { 'imgUrl': catList.img,
          'title': catList.title,
          'minSoldNum': catList.minSoldNum,
          'price': catList.price
        })
    },
    handleScroll () {
      const scroll = this.$refs.box.offsetTop
      Link.$emit('val2', scroll)
    }
  },
  mounted () {
    this.getHomeInfo()
    window.addEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="scss" scoped>
  @import '~@/assets/styles/varible.scss';
  @import '~@/assets/styles/category.scss';
</style>
