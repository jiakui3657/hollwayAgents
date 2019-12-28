<template>
  <div class="container">
    <van-image class="logo" :src="login" />
    <div class="login">
      <van-field id="input" v-model="user" placeholder="请输入账号" />
      <van-field
        id="input"
        v-model="pass"
        type="password"
        placeholder="请输入密码"
      />
      <van-button id="btn" type="info" @click="sumbit">登录</van-button>
    </div>
  </div>
</template>

<script>
export default {
  name: "login",
  components: {},
  data() {
    return {
      user: "13468844686",
      pass: "111111",
      login: require("../assets/login.jpg")
    };
  },
  methods: {
    sumbit: function() {
      this.$router.push("home");
    }
  }
};
</script>

<style lang="less">
.container {
  height: 100%;
}

.logo {
  width: 100%;
  height: 10rem;
  display: block;
}

.login {
  padding: 0.96rem 0.8rem;
  box-sizing: border-box;
  width: 100%;
}

#btn {
  min-width: 100%;
  color: #fff;
  justify-content: center;
  display: flex;
  align-items: center;
  border-radius: 3px;
  padding: 0;
  margin: 0;
  margin-top: 2.13rem;
  background: #3fa2f5;
}
</style>
