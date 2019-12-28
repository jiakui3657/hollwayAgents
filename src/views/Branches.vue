<template>
  <div class="branches">
    <van-pull-refresh v-model="isLoading" @refresh="onRefresh">
      <van-list
        v-model="loading"
        :finished="finished"
        finished-text="没有更多了"
        @load="onLoad"
      >
        <van-cell class="branchesList" v-for="(item, index) in 10" :key="index" @click.stop="branchDetails">
          <div class="shopName">
            <div>2068香辣虾</div>
            <div>13468844686</div>
          </div>
          <div class="shopTime">
            <div>服务时间: 06-22</div>
            <div>创建人： 贾魁</div>
          </div>
          <div class="shopAddress">陕西省西安市雁塔区科技路西口陈家庄小区</div>
          <div class="shopEarnings">
            <div>今日收益： ￥22</div>
            <div>本月收益： ￥220</div>
            <div>总收益： ￥242</div>
          </div>
          <div class="special">
            <div class="product">
              <div>产品类型： 充电宝</div>
              <div>设备ID： JIAKUI3657</div>
            </div>
            <div class="func">
              <div @click.stop="branches_details">
                <img :src="require('../assets/editor.jpg')" alt="" />
                <span>编辑</span>
              </div>
              <div @click.stop="branchesManagement">
                <img :src="require('../assets/management.jpg')" alt="" />
                <span>管理</span>
              </div>
              <div class="del" @click.stop="del">
                <img :src="require('../assets/del.jpg')" alt="" />
                <span>删除</span>
              </div>
            </div>
          </div>
          <div class="setUp">
            <div @click.stop="addEquipment">创建设备</div>
            <div @click.stop="vip_members">会员设置</div>
          </div>
        </van-cell>
      </van-list>
    </van-pull-refresh>
    <div class="btn" @click.stop="create_branches">创建网点</div>
  </div>
</template>

<script>
export default {
  name: "branches",
  components: {},
  data() {
    return {
      isLoading: false,
      loading: false,
      finished: false
    };
  },
  methods: {
    del() {
      this.$dialog.confirm({
        title: '标题',
        message: '是否删除网店'
      }).then(() => {
        // on confirm
      }).catch(() => {
        // on cancel
      });
    },
    branchesManagement() {
      this.$router.push("branchesManagement");
    },
    addEquipment() {
      this.$router.push("addEquipment");
    },
    branchDetails() {
      this.$router.push("branchDetails");
    },
    vip_members() {
      this.$router.push("vipMembers");
    },
    onLoad() {
      // 异步更新数据
      setTimeout(() => {
        // 加载状态结束
        this.loading = false;
        this.finished = true;
      }, 500);
    },
    onRefresh() {
      setTimeout(() => {
        this.$toast.success("刷新成功");
        this.isLoading = false;
      }, 500);
    },
    create_branches() {
      this.$router.push("createBranches");
    },
    branches_details() {
      this.$router.push("branchesDetails");
    }
  }
};
</script>

<style lang="less">
.branches {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  min-height: 100%;
  background: #f5f5f5;
  padding-bottom: 2.61rem;
  box-sizing: border-box;
  .branchesList {
    margin-top: 0.53rem;
    background: #fff;
    width: 100%;
    padding: 1.21rem 1.01rem;
    box-sizing: border-box;
    font-size: 0.75rem;
    color: #101010;
    &:first-child {
      margin-top: 0;
    }
  }

  .shopName,
  .shopTime,
  .shopAddress {
    display: flex;
    margin-top: 0.32rem;
  }

  .shopName {
    margin-top: 0rpx;
  }

  .shopName div {
    width: 50%;
    display: flex;
    align-items: center;
  }

  .shopTime div {
    width: 50%;
    display: flex;
    align-items: center;
  }

  .shopEarnings {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    margin-top: 0.32rem;
  }

  .special {
    display: flex;
    justify-content: space-between;
  }

  .product {
    display: flex;
    flex-direction: column;
    flex: 1;
    text-align: left;
    div {
      margin-top: 0.32rem;
    }
  }

  .func {
    display: flex;
    justify-content: space-between;
    width: 30%;
    div {
      box-sizing: border-box;
      font-size: 0.64rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      &:last-child {
        color: #b43b44;
      }
    }
    img {
      width: 1.12rem;
      height: 1.12rem;
      display: block;
    }
  }

  .setUp {
    display: flex;
    justify-content: center;
    margin-top: 0.8rem;
    div {
      width: 5.6rem;
      height: 1.86rem;
      border-radius: 3px;
      color: #fff;
      background: #3f88e7;
      font-size: 0.7rem;
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 0 1.33rem;
    }
  }

  .btn {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 2.61rem;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    font-size: 0.85rem;
    background: #3f88e7;
  }
}
</style>
