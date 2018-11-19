<template>
  <div id="operhead">
    <div class="wrapper">
      <h2>全部商品 12</h2>
      <table>
        <tr>
          <td><input type="checkbox" class="in_checkbox"/>全选</td>
          <td>商品信息</td>
          <td>蚂蚁价</td>
          <td>数量</td>
          <td>总价</td>
          <td>操作</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CartOperhead'
}
</script>

<style lang="scss" scoped>
@import '~@/assets/styles/varible';
#operhead {
  margin-bottom: 30px;
  @extend %wrapper;
  h2, table {
    height: 50px;
    line-height: 50px;
  }
  h2 {
    font-size: 16px;
    padding-left: 20px;
  }
  table {
    width: 100%;
    background-color: rgba(242,242,242,1);
    tr {
      display: block;
      padding-left: 20px;
      td {
        width: 195px;
        font-size: 14px;
        font-weight: normal;
        text-align: center;
        @extend %checkbox;
      }
      td:first-child {
        text-align: left;
      }
    }
  }
}
</style>
