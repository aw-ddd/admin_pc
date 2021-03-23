<template>
  <div class="login-back">
    <el-card class="login-card">
      <el-form>
        <el-form-item label="用户名">
          <el-input label="用户名" v-model="user.username"></el-input>
        </el-form-item>
        <el-form-item label="密码">
          <el-input label="密码" v-model="user.password" show-password></el-input>
        </el-form-item>
        <el-button @click="login" >登录</el-button>
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      user: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    login() {
      this.$request.post('/user/login', this.user).then(e => {
        //将登录成功之后的值返回到sessionStorage中
        if (e.data.success) {
          window.sessionStorage.setItem("token", e.data.data)
          this.$message.success(e.data.errorMsg)
        } else {
          this.$message.error(e.data.errorMsg)
        }
      })
    }
  }
}
</script>

<style scoped>
.login-back {
}

.login-card {
  background-color: #a1aebf;
  margin: 100px auto;
  width: 500px;
}
</style>
