<template>
  <div id="search">
    <div class="wrapper">
      <div class="box">
        <span class="logo_text">{{logoFont}}</span>

        <div class="search_logo">
          <main>
            <a class="logo_img"><img src="http://pifa.yunmayi.com/statics/images/new_log.png" title="云蚂蚁www.yunmayi.com"/></a>
            <a class="logo_font">
              <img src="http://pifa.yunmayi.com/statics/images/index/04171124.png" title="云蚂蚁批发平台"/>
            </a>
          </main>
        </div>

        <div class="search_form">
            <input type="text" placeholder="搜索商品关键字，品牌"/>
            <button type="submit">搜索</button>
        </div>
        <!--购物车组件start-->
        <Cart class="search_cart"></Cart>
        <!--购物车组件end-->
        <div class="search_img">
          <img src="../../assets/imgs/2.png" alt="云蚂蚁app二维码" title="扫码下载云蚂蚁官方APP"/>
        </div>
      </div>

      <div class="search_bar">
        <section class="bar_section">
          <h2>全部商品分类</h2>
          <!--全部商品分类组件-->
          <fix-catalog></fix-catalog>
        </section>

        <ul class="search_bar_ul">
          <li><a href="">首页</a></li>
          <li v-for="item of goodsList" :key="item.id"><a href="">{{item.name}}</a></li>
        </ul>

      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Link from './public_js/link.js'
import FixCatalog from './Fixcatalog'
export default {
  name: 'HomeSearcher',
  components: {
    FixCatalog
  },
  props: {
    logoFont: String
  },
  data () {
    return {
      cartNum: 0,
      cartList: [],
      newArr: [],
      goodsList: [
        {
          'name': '酒水饮料',
          'id': '1001',
          'items': [
            {
              'secName': '饮料',
              'id': '1051',
              'goods': ['碳酸饮料', '果汁饮料', '茶饮料', '机能型饮料', '水', '乳脂饮料']
            },
            {
              'secName': '啤酒',
              'id': '1052',
              'goods': ['国产听装啤酒', '国产瓶装啤酒', '进口酒']
            },
            {
              'secName': '果酒',
              'id': '1053',
              'goods': ['干红', '桃红', '其它']
            }
          ]
        },
        {
          'name': '食品零食',
          'id': '1002',
          'items': [
            {
              'secName': '膨化食品',
              'id': '1051',
              'goods': ['薯片', '海苔']
            },
            {
              'secName': '饼干点心',
              'id': '1052',
              'goods': ['梳打', '夹心', '威化']
            }, {
              'secName': '方便食品',
              'id': '1053',
              'goods': ['袋装', '桶装', '其它']
            }
          ]
        },
        {
          'name': '粮油调味',
          'id': '1003',
          'items': [
            {
              'secName': '调味品',
              'id': '1051',
              'goods': ['盐', '原糖', '烹饪油']
            }, {
              'secName': '粮食干货',
              'id': '1052',
              'goods': ['大米', '面粉', '杂粮']
            }, {
              'secName': '水产干货',
              'id': '1053',
              'goods': ['水产']
            }
          ]
        },
        {
          'name': '日用洗护',
          'id': '1004',
          'items': [
            {
              'secName': '洗发用品',
              'id': '1051',
              'goods': ['洗发', '美发']
            },
            {
              'secName': '洗浴用品',
              'id': '1052',
              'goods': ['香皂', '沐浴露']
            },
            {
              'secName': '口腔护理',
              'id': '1053',
              'goods': ['牙刷', '牙膏']
            }
          ]
        },
        {
          'name': '家用百货',
          'id': '1005',
          'items': [
            {
              'secName': '日用杂品',
              'id': '1051',
              'goods': ['塑料', '玻璃烟灰缸']
            }, {
              'secName': '针绵用品',
              'id': '1052',
              'goods': ['男女内衣裤', '毛巾鞋袜']
            }
          ]
        },
        {
          'name': '冰淇淋',
          'id': '1006',
          'items': [
            {
              'secName': '冰棒类',
              'id': '1051',
              'goods': ['冰棒']
            }, {
              'secName': '蛋筒类',
              'id': '1052',
              'goods': ['蛋筒']
            }, {
              'secName': '其它',
              'id': '1053',
              'goods': ['其它']
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
        this.cartNum = data.cartNum
        this.cartList = data.cartList
        this.goodsList = data.goodsList
      }
    }
  },
  mounted () {
    this.getHomeInfo()
    const vm = this
    Link.$on('val', (dat) => {
      // vm.total = dat
      vm.newArr.push(dat)
    })
  }
}
</script>

<style lang="scss" scoped>
  @import '~@/assets/styles/varible';
  #search .bar_section:hover {
    /deep/ .fixcatalog {
      display: block;
    }
  }
  #search {
    @extend %wrapper;
    height: 150px;
    background-color: $bgColor2;
    box-shadow: 0 -1px 0 0 rgba(217,217,217,1);
    border-bottom: 2px solid rgba(230,45,45,1);
    .box {
        height: 120px;
        position: relative;
        .logo_text {
          position: absolute;
          top: 45px;
          left: 109px;
          font-size: 30px;
          color: rgba(51,51,51,1);
          text-indent: 13px;
          display: none;
        }
        .search_logo {
          width: 230px;
          height: 100px;
          float: left;
          padding-top: 20px;
          margin-right: 60px;
          main {
            width: 220px;
            height: 76px;
            padding: 0 6px 0 4px;
            a {
              float: left;
              display: inline-block;
              img {
                width: 100%;
                vertical-align: middle;
              }
            }
            .logo_img { width: 96px; }
            .logo_font {
              width: 124px;
              line-height: 76px;
              height: 76px;
              display: block;
            }
          }
        }

        .search_form {
          width: 546px;
          height: 36px;
          line-height: 36px;
          border: 2px solid rgba(230,45,45,1);
          float: left;
          margin-top: 47px;
          input {
            font-size: 14px;
            width: 452px;
            color: rgba(153,153,153,1);
            background-color: inherit;
            border: none;
            padding-left: 12px;
          }
          button {
            outline: none;
            border: none;
            background-color: rgba(230,45,45,1);
            width: 80px;
            height: 36px;
            float: right;
            font-size: 18px;
            color: rgba(255,255,255,1);
            cursor: pointer;
          }
          button:active { background-color: rgba(230,45,45,.6); color: rgba(255,255,255,.4);}
        }
        .search_img {
          width: 70px;
          height: 70px;
          float: left;
          margin-top: 31px;
          img {
            width: 100%;
            height: 100%;
          }
        }
    }
    .search_bar {
      height: 30px;
      line-height: 30px;
      width: 100%;
      float: left;
      .bar_section {
        background-color: rgba(230, 45, 45, 1);
        color: $color;
        display: inline-block;
        width: 230px;
        float: left;
        cursor: pointer;
        h2 {
          font-size: 16px;
          text-align: center;
        }
      }

      .search_bar_ul {
        display: inline-block;
        width: 720px;
        height: 30px;
        overflow: hidden;
        li {
          float: left;
          padding-left: 30px;
          a {
            color: rgba(51, 51, 51, 1);
          }
          a:hover {
            color: #ff0000;
            background-color: #f2f2f2;
          }
        }
      }

      .search_bar_hide {
        width: 230px;
        height: 100px;
        background: red;
      }
    }
  }
</style>
