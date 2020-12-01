<template>
  <div class="login-container">
    <div class="background-form-wrapper" />
    <div class="login-form-wrapper">
      <el-form ref="loginForm" :model="loginForm" :rules="loginRules" class="login-form" auto-complete="on" label-position="left">
        <div class="title-container">
          <h3 class="title">生产制造执行管理系统</h3>
        </div>

        <el-form-item class="login-form-item" prop="username">
          <el-input
            ref="username"
            v-model="loginForm.username"
            size="large"
            placeholder="用户名"
            name="username"
            type="text"
            tabindex="1"
            auto-complete="on"
          >
            <template v-slot:prepend>
              <i class="el-icon-user" />
            </template>
          </el-input>
        </el-form-item>

        <el-form-item prop="password">
          <el-input
            :key="passwordType"
            ref="password"
            v-model="loginForm.password"
            size="large"
            :type="passwordType"
            placeholder="密码"
            name="password"
            tabindex="2"
            auto-complete="on"
            @keyup.enter.native="handleLogin"
          >
            <template v-slot:prepend>
              <i class="el-icon-lock" />
            </template>
          </el-input>
        </el-form-item>

        <el-button size="medium" :loading="loading" type="primary" style="width:100%;margin-top: 16px" @click.native.prevent="handleLogin">登陆</el-button>
      </el-form>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {

    }
  },
  methods: {

  }
}
</script>

<style scoped>

</style>
