<template>
  <div id="onself">
    <div class="wrapper">
      <h2><input type="checkbox" class="in_checkbox"/>该订单由供应商<span>【悦冰冻品自主配送】</span>提供配送</h2>
      <table>
        <tr>
          <td class="td_first">
            <input type="checkbox" class="in_checkbox"/>
            <div class="img_box">
              <img src="http://pifa.yunmayi.com/upload/2015/10/21/165dfcb4125eec29a429f10ce8e45e5c.jpg"/>
            </div>
          </td>
          <td>奥雪131草莓牛奶口味冰淇淋78g（连锁）</td>
          <td>¥28.00</td>
          <td>
            <div class="flex">
              <a href="javascript:;" class="reduce">-</a>
              <input type="text" placeholder="8" readonly/>
              <a href="javascript:;" class="plus">+</a>
            </div>
            <h3>限购10箱</h3>
          </td>
          <td>¥224.00</td>
          <td>
            <p>删除</p>
            <p>移入收藏中心</p>
          </td>
          <td class="gift">
            <div class="gift_title">赠送</div>
            <div class="gift_img"><img src="http://pifa.yunmayi.com/upload/2015/10/21/165dfcb4125eec29a429f10ce8e45e5c.jpg"/></div>
            <span class="gift_text">
                奥宇羊奶原味冰激凌雪糕棒冰78g杯（连锁）
                <a>再买2箱</a>
                <i>即可获赠百事可乐灌装250ml*24罐</i>
                <a>2箱</a>
              </span>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CartOneself'
}
</script>

<style lang="scss" scoped>
@import '~@/assets/styles/varible';
#onself {
  @extend %wrapper;
  @extend %checkbox;
  h2 {
    height: 20px;
    line-height: 20px;
    font-size: 16px;
    font-weight: normal;
    margin-bottom: 10px;
    border-left: 4px red solid;
    text-indent: 16px;
  }
  table {
    width: 100%;
    tr {
      padding: 20px 0 20px 20px;
      border: 1px dashed #7C7E80;
      font-size: 14px;
      display: block;
      td {
        width: 195px;
        text-align: center;
        vertical-align: top;
      }
      td.td_first {
        text-align: left;
        .in_checkbox {
          float: left;
        }
        .img_box {
          display: inline-block;
          width: 90px;
          height: 90px;
          border: 1px solid #F2F2F2;
          img {
            width: 100%;
            height: 100%;
          }
        }
      }
      td .flex {
        display: flex;
        width: 110px;
        margin: 0 auto;
        a {
          width: 30px;
          height: 30px;
          display: inline-block;
          line-height: 30px;
          border: 1px solid #c4c4c4;
        }
        a.reduce {
          border-right: none;
        }
        a.plus {
          border-left: none;
        }
        input {
          width: 50px;
          text-align: center;
          flex: 1;
          border: 1px solid #C4C4C4;
        }
      }
      td h3 {
        color: rgba(153,153,153,1);
        margin-top: 14px;
        font-size: 14px;
        font-weight: normal;
      }
      .gift {
        position: absolute;
        width: auto;
        margin-left: 70px;
        .gift_title {
          display: inline-block;
          width: 57px;
          height: 40px;
          border-left: 1px solid #F2F2F2;
          border-bottom: 1px solid #f2f2f2;
        }
        .gift_img {
          width: 44px;
          height: 44px;
          display: inline-block;
          img {
            width: 100%;
            height: 100%;
          }
        }
      }
    }
  }
}
</style>
