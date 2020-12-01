<template>
  <q-layout>
    <q-page-container>
      <q-page class="flex bg-image flex-center">
        <q-card v-bind:style="$q.screen.lt.sm?{'width': '60%'}:{'width':'30%'}">
          <q-card-section>
            <q-avatar size="103px" class="absolute-center  shadow-10">
              <img src="../../assets/login/profile.svg">
            </q-avatar>
          </q-card-section>

          <q-card-section>
            <div class="text-center q-pt-lg">
              <div class="col text-h6 ellipsis">
                系统登录
              </div>
            </div>
          </q-card-section>

          <q-card-section>
            <q-form
              class="q-gutter-md"
              @submit="onSubmit"
              @reset="onReset"
              ref="loginForm"
            >
              <q-input
                filled
                v-model="formData.username"
                label="用户名"
                lazy-rules
                :rules="[ val => val && val.length > 0 || '请输入用户名']"
              />

              <q-input
                type="password"
                filled
                v-model="formData.password"
                label="密码"
                lazy-rules
                :rules="[
                  val => val && val.length > 0 || '请输入密码',
                  val => val && val.length === 6 || '请输入6位密码'
                ]"
              />

              <div>
                <q-btn :loading="submitLoading" label="登录" type="submit" color="primary" style="left: 50%;transform: translate(-50%,-50%);margin-top: 20px;" />
              </div>
            </q-form>
          </q-card-section>
        </q-card>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      formData: {
        username: undefined,
        password: undefined
      },
      submitLoading: false
    }
  },
  methods: {
    // 提交表单
    onSubmit () {
      debugger
      this.$refs.loginForm.validate().then(success => {
        if (success) {
          this.submitLoading = true
        }
      })
    },
    // 重置表单
    onReset () {
      this.formData = {}
      this.$refs.loginForm.resetValidation()
    }
  }
}
</script>

<style scoped>
.bg-image {
  background:url('../../assets/login/login_bg.jpg') no-repeat;
  background-size: cover;
}
</style>
