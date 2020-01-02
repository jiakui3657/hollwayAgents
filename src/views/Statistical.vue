<template>
  <div class="statistical">
    <div class="search">
      <van-field
        readonly
        clickable
        :value="currentTime"
        placeholder="结束时间"
        @click="timeState = true"
      />

      <van-popup v-model="timeState" position="bottom">
        <van-datetime-picker
          v-model="currentTime"
          type="time"
          :min-hour="0"
          :max-hour="23"
          @confirm="getCurrentTime"
          @cancel="timeState = false"
        />
      </van-popup>
      <span>搜索</span>
    </div>
    <div class="content">
      <div class="dataList">
        <div class="dataList_l dataItem">
          <div class="">{{ statisticsInfo.orderNum }}<span>单</span></div>
          <div>生成订单</div>
        </div>
        <div class="dataList_r dataItem">
          <div class="">{{ statisticsInfo.money }}<span>元</span></div>
          <div>创造收益</div>
        </div>
      </div>
      <div class="dataList">
        <div class="dataList_l dataItem">
          <div class="">{{ statisticsInfo.deviceNum }}<span>个</span></div>
          <div>创建网点</div>
        </div>
        <div class="dataList_r dataItem">
          <div class="">{{ statisticsInfo.teamNum }}<span>人</span></div>
          <div>新增团队</div>
        </div>
      </div>
    </div>
    <TabBar v-bind:index="1" />
  </div>
</template>

<script>
// @ is an alias to /src
import TabBar from "@/components/TabBar.vue";

export default {
  name: "statistical",
  components: {
    TabBar
  },
  data() {
    return {
      currentTime: "00:00",
      statisticsInfo: {},
      timeState: false
    };
  },
  mounted: function() {
    this.getStatisticsInfo();
  },
  methods: {
    getStatisticsInfo(beginDate = "", endDate = "") {
      let _this = this;
      let params = {
        beginDate,
        endDate
      };
      _this.https
        .fetchPost("/rest/agent/statistics.htm", params)
        .then(data => {
          if (data.code == 0) {
            window.console.log(data);
            _this.statisticsInfo = data;
          } else {
            this.$toast(data.msg);
          }
        })
        .catch(err => {
          window.console.log(err);
        });
    },
    getCurrentTime(value) {
      window.console.log(value);
      this.currentTime = value;
      this.timeState = false;
    }
  }
};
</script>

<style lang="less">
.statistical {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: #f5f5f5;
  .van-cell {
    padding: 0;
  }
}

.search {
  width: 100%;
  height: 2.4rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-sizing: border-box;
  background: #5ba0ee;
  padding: 0 0.75rem;
}

.search input {
  flex: 1;
  height: 1.33rem;
  font-size: 0.75rem;
  color: #101010;
  background: #fff;
  border: 0;
  padding: 0;
  padding-left: 0.4rem;
}

::-webkit-input-placeholder {
  font-size: 0.65rem;
  color: #ccc;
}

.search span {
  font-size: 0.75rem;
  color: #101010;
  width: 2.61rem;
  height: 1.33rem;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: 0.75rem;
}

.content {
  margin-top: 0.53rem;
  background: #fff;
  width: 100%;
  box-sizing: border-box;
  padding: 1.06rem 0.75rem;
}

.dataList {
  width: 100%;
  margin-top: 0.53rem;
  display: flex;
  justify-content: space-between;
  background: #cccccc;
  border-radius: 5px;
  height: 3.57rem;
}

.dataList:first-child {
  margin-top: 0;
}

.dataList_l,
.dataList_r {
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-size: 0.75rem;
  color: #838383;
}

.dataItem view:first-child text {
  font-size: 0.75rem;
  margin-left: 0.16rem;
}

.dataItem view:first-child {
  font-size: 1.23rem;
  color: #f9827a;
}

.name {
  font-size: 0.85rem;
  color: #313131;
}

.title {
  font-size: 0.75rem;
  color: #8b8b8b;
}
</style>
