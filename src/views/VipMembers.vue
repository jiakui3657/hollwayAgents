<template>
  <div class="vipMembers">
    <div class="item">
      <div class="itemLeft">
        <span>*</span>
        负责人：
      </div>
      <div class="itemRight">
        <van-field
          maxlength="5"
          v-model="name"
          placeholder="请输入负责人名称"
        />
      </div>
    </div>
    <div class="item">
      <div class="itemLeft">
        <span>*</span>
        所属行业：
      </div>
      <div class="itemRight">
        <van-field
          readonly
          clickable
          :value="industry"
          placeholder="选择行业"
          @click="industryPicker = true"
        />
        <van-popup v-model="industryPicker" position="bottom">
          <van-picker
            show-toolbar
            :columns="industryList"
            @cancel="industryPicker = false"
            @confirm="industryChange"
          />
        </van-popup>
      </div>
    </div>
    <div class="item">
      <div class="itemLeft">
        <span>*</span>
        商家分类：
      </div>
      <div class="itemRight">
        <van-field
          readonly
          clickable
          :value="shop"
          placeholder="选择商家类型"
          @click="shopPicker = true"
        />
        <van-popup v-model="shopPicker" position="bottom">
          <van-picker
            show-toolbar
            :columns="shopList"
            @cancel="shopPicker = false"
            @confirm="shopChange"
          />
        </van-popup>
      </div>
    </div>
    <div class="item">
      <div class="itemLeft">
        <span>*</span>
        折扣比例：
      </div>
      <div class="itemRight">
        <van-field v-model="discount" placeholder="8即是8折" />
      </div>
    </div>
    <div class="item">
      <div class="itemLeft">
        <span>*</span>
        商家logo：
      </div>
      <div class="itemRight logo">
        <van-uploader :after-read="afterLogo" />
      </div>
    </div>
    <div class="item">
      <div class="itemLeft">
        <span>*</span>
        商家门头：
      </div>
      <div class="itemRight logo">
        <van-uploader :after-read="afterBanner" />
      </div>
    </div>
    <div class="item">
      <div class="itemLeft">
        <span>*</span>
        会员特权：
      </div>
      <div class="itemRight">
        <van-field maxlength="30" placeholder="30字限制" />
      </div>
    </div>
    <div class="item">
      <div class="itemLeft">
        <span>*</span>
        商家简介：
      </div>
      <div class="itemRight">
        <van-cell-group>
          <van-field
            v-model="shopInfo"
            rows="1"
            autosize
            type="textarea"
            maxlength="100"
            placeholder="100字限制"
          />
        </van-cell-group>
      </div>
    </div>
    <div class="btn" @click="btn">提交</div>
  </div>
</template>

<script>
export default {
  name: "vipMembers",
  components: {},
  data() {
    return {
      name: "",
      discount: "",
      industry: "",
      shopInfo: "",
      industryPicker: false,
      industryList: ["杭州", "宁波", "温州", "嘉兴", "湖州"],
      shop: "",
      shopPicker: false,
      shopList: ["杭州", "宁波", "温州", "嘉兴", "湖州"]
    };
  },
  methods: {
    afterLogo(file) {
      window.console.log(file);
    },
    afterBanner(file) {
      window.console.log(file);
    },
    industryChange(picker) {
      window.console.log(picker);
      this.industry = picker;
      this.industryPicker = false;
    },
    shopChange(picker) {
      this.shop = picker;
      this.shopPicker = false;
    },
    btn() {
      this.$router.go(-1);
    }
  }
};
</script>

<style lang="less">
.vipMembers {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  min-height: 100%;
  padding-bottom: 2.61rem;
  box-sizing: border-box;
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
    margin-top: 1.33rem;
  }

  .itemLeft {
    width: 4.26rem;
    display: flex;
    align-items: center;
    height: 100%;
    margin-right: 0.64rem;
  }

  .itemLeft span {
    color: #ec1d39;
    margin-right: 0.21rem;
    display: flex;
  }

  .itemRight {
    box-sizing: border-box;
    flex: 1;
    min-height: 2.24rem;
    display: flex;
    align-items: center;
    border-bottom: 1px solid #dedede;
  }

  .van-field {
    display: flex;
    align-items: center;
    height: 100%;
  }

  .van-cell-group {
    width: 100%;
    &:after {
      border: 0;
    }
  }

  .logo,
  .door {
    border: 0;
    height: auto;
  }

  .logo img {
    width: 4rem;
    height: 4rem;
    display: block;
  }

  .door img {
    height: 5.33rem;
    width: 13.33rem;
    display: block;
  }

  .btn {
    min-width: 100%;
    height: 2.61rem;
    font-size: 0.85rem;
    color: #fff;
    justify-content: center;
    display: flex;
    align-items: center;
    border-radius: 3px;
    padding: 0;
    margin: 2.13rem 0;
    background: #3fa3f8;
  }
}
</style>
