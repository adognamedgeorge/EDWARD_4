<template>
  <div id="cart" class="wrapper">
    <Header></Header>
    <Searcher :logoFont="logoFont"></Searcher>
    <cart-operhead></cart-operhead>
    <cart-onself></cart-onself>
  </div>
</template>

<script>
import CartOperhead from './components/Operhead'
import CartOnself from './components/Onself'
export default {
  name: 'Cart',
  data () {
    return {
      logoFont: '购物车'
    }
  },
  components: {
    CartOperhead,
    CartOnself
  }
}
</script>

<style lang="scss" scoped>
#cart /deep/ .search_img {
  display: none;
}
#cart /deep/ .search_cart {
  display: none;
}
#cart /deep/ .search_bar {
    display: none;
  }
#cart /deep/ .search_form {
  float: right !important;
  overflow: hidden;
}
#cart /deep/ .logo_font {
  img {
    display: none;
  }
}
#cart /deep/ .logo_text {
  display: block !important;
}
#cart /deep/ #search {
  height: 130px;
  border-bottom: unset;
  box-shadow: 0 1px 0 0 rgba(217,217,217,1);
}
</style>
