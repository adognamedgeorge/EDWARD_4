<template>
  <div id="slider">
    <div class="wrapper">
      <!--全部商品分类子组件-->
      <home-catalog :goodsList="goodsList"></home-catalog>
      <!--vue-awesome-swiper插件轮播-->
      <div class="lunb">
        <swiper :options="swiperOption" v-if="showSwiper">
          <swiper-slide v-for="item of posterList" :key="item.sort">
            <a :href="item.link" target="_blank"><img class="swiper_img" :src="item.img"/></a>
          </swiper-slide>
          <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
      </div>
      <!--签到板块子组件-->
      <home-sign :account="account" :noticeList="noticeList"></home-sign>
    </div>
  </div>
</template>

<script>
import HomeCatalog from './Catalog'
import HomeSign from './Sign'
import axios from 'axios'
export default {
  name: 'HomePoster',
  components: {
    HomeCatalog,
    HomeSign
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true,
        paginationClickable: true,
        speed: 3000,
        autoplayDisableOnInteraction: false,
        mousewheelControl: true,
        autoplay: 1000,
        paginationBulletRender: function (swiper, index, className) {
          return '<span class="' + className + '">' + (index + 1) + '</span>'
        }
      },
      // goodsList: [],
      // posterList: [],
      account: {},
      noticeList: [],
      goodList: [
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
      ],
      posterList: [
        {
          'img': 'http://p1.music.126.net/CEznnRcRcLpen07YSbMD3g==/109951163517815037.jpg',
          'link': 'http://pifa.yunmayi.com/notice/detail?id=168',
          'sort': 0
        },
        {
          'img': 'http://p1.music.126.net/3ovn332Vy0MsvA3Q8kWvOw==/109951163515911854.jpg',
          'link': 'http://pifa.yunmayi.com/notice/detail?id=169',
          'sort': 1
        }]
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
        this.goodsList = data.goodsList
        this.posterList = data.posterList
        this.account = data.account
        this.noticeList = data.noticeList
      }
    }
  },
  computed: {
    showSwiper () {
      return this.posterList.length
    }
  },
  mounted () {
    this.getHomeInfo()
  }
}
</script>

<style lang="scss" scoped>
  @import '~@/assets/styles/varible.scss';
  #slider /deep/ .swiper-pagination-bullet {
    width: 20px;
    height: 20px;
    background-color: rgba(0, 0, 0, 0.8);
    opacity: .8;
    filter: Alpha(opacity=80);
    line-height: 20px;
    text-align: center;
    margin-right: 10px;
    margin-left: unset;
    color: #fff;
    font-size: 14px;
    cursor: pointer;
  }
  #slider /deep/ .swiper-pagination-bullets {
    left: unset;
    width: unset;
    right: 20px;
  }
  #slider /deep/ .swiper-pagination-bullet-active { background-color: rgba(230,45,45,1); }

  #slider {
    height: 330px;
    padding-bottom: 10px;
    background-color: $bgColor3;
    @extend %wrapper;
    .wrapper {
      display: flex;
      display: -ms-flexbox;
    }

    .lunb {
      overflow: hidden;
      width: 700px;
      height: 320px;
      background: #fff;
      margin: 10px 10px 0 10px;
      .swiper_img {
        width: 100%;
        height: 100%;
      }
      .swiper_container {
        height: 100%;
        z-index: 0;
      }
    }
  }
</style>
