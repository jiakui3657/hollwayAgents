<template>
  <div class="branchDetails">
    <div class="item">
      <div class="itemLeft">
        商家名称：
      </div>
      <div class="itemRight">2068香辣虾</div>
    </div>
    <div class="item">
      <div class="itemLeft">
        负责人：
      </div>
      <div class="itemRight">贾魁</div>
    </div>
    <div class="item">
      <div class="itemLeft">
        联系电话：
      </div>
      <div class="itemRight">13468844686</div>
    </div>
    <div class="item">
      <div class="itemLeft">
        商家分类：
      </div>
      <div class="itemRight">会员商家</div>
    </div>
    <div class="item">
      <div class="itemLeft">
        商家折扣：
      </div>
      <div class="itemRight">8折</div>
    </div>
    <div class="item">
      <div class="itemLeft">
        商家LOGO：
      </div>
      <div class="itemRight logo">
        <img :src="require('../assets/logo.jpg')" alt="" srcset="">
      </div>
    </div>
    <div class="item">
      <div class="itemLeft">
        商家门头：
      </div>
      <div class="itemRight door">
        <img :src="require('../assets/logo.jpg')" alt="" srcset="">
      </div>
    </div>
    <div class="item">
      <div class="itemLeft">
        会员地址：
      </div>
      <div class="itemRight">陕西省西安市雁塔区陈家庄小区</div>
    </div>
     <div class="item">
      <div class="itemLeft">
        会员特权：
      </div>
      <div class="itemRight">荷尔盟会员享受全场8折优惠!</div>
    </div>
    <div class="item">
      <div class="itemLeft">
        商家简介：
      </div>
      <div class="itemRight">欢迎光临2068香辣虾!</div>
    </div>
     <div class="item">
      <div class="itemLeft">
        上线日期：
      </div>
      <div class="itemRight">10-25</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "branchDetails",
  components: {},
  data() {
    return {};
  },
  methods: {}
};
</script>

<style lang="less">
.branchDetails {
  position: absolute;
  top: 0;
  left: 0;
  min-height: 100%;
  display: flex;
  flex-direction: column;
  padding: 0 0.8rem;
  box-sizing: border-box;
  .item {
    display: flex;
    min-height: 2.24rem;
    align-items: center;
    font-size: 0.7rem;
    color: #151412;
  }

  .itemLeft {
    width: 4.26rem;
    display: flex;
    align-items: center;
    height: 100%;
    margin-right: 0.64rem;
    span {
      color: #ec1d39;
      margin-right: 0.21rem;
      display: flex;
    }
  }

  .itemRight {
    box-sizing: border-box;
    flex: 1;
    min-height: 2.24rem;
    display: flex;
    align-items: center;
  }

  .logo, .door {
    border: 0;
    height: auto;
  }

  .logo img {
    width: 4rem;
    height: 4rem;
    display: block;
    margin: 0.53rem 0;
  }

  .door img {
    height: 5.33rem;
    width: 13.33rem;
    display: block;
  }
}
</style>
