<template>
  <div id="poster">
    <el-container>
      <el-header height="200px"></el-header>
      <el-main>
        <el-row>
          <el-col :span="14">
            <div>
            </div>
          </el-col>
          <el-col :span="10">
            <el-tabs v-model="defaultTab" type="border-card" :stretch="true" id="login">
              <el-tab-pane name="msg" label="短信登录/注册">
                <el-form ref="form" :model="user" label-width="80px" label-position="left" style="margin: 20px">
                  <el-form-item label="账号">
                    <el-input v-model="user.name"></el-input>
                  </el-form-item>
                  <el-form-item label="密码">
                    <el-input v-model="user.pwd" show-password></el-input>
                  </el-form-item>
                </el-form>
                <el-button type="primary" plain @click="register">注册</el-button>
              </el-tab-pane>
              <el-tab-pane name="pwd" label="密码登录">
                <el-form ref="form" :model="user" label-width="80px" label-position="left" style="margin: 20px">
                  <el-form-item label="账号">
                    <el-input v-model="user.name"></el-input>
                  </el-form-item>
                  <el-form-item label="密码">
                    <el-input v-model="user.pwd" show-password></el-input>
                  </el-form-item>
                </el-form>
                <el-button type="primary" plain @click="login">登录</el-button>
              </el-tab-pane>
            </el-tabs>
          </el-col>
        </el-row>
      </el-main>
    </el-container>
  </div>
</template>

<script>
export default {
  name: 'AppIndex',
  data () {
    return {
      defaultTab: 'pwd',
      user: {
        name: '',
        pwd: ''
      }
    }
  },
  methods: {
    // TODO：封装AXIOS
    login () {
      this.$axios({
        method: 'post',
        url: 'login',
        data: {
          username: this.user.name,
          password: this.user.pwd
        }
      }).then(successResponse => {
        if (successResponse.data.code === 200) {
          this.$notify({
            title: '成功',
            message: '登录成功！',
            type: 'success'
          })
          this.$router.push('/')
        } else {
          this.$notify.error({
            title: '错误',
            message: '登陆失败！'
          })
        }
      }).catch(failResponse => {
        this.$notify.error({
          title: '错误',
          message: '登陆失败！'
        })
      })
    },
    register () {
      this.$axios({
        method: 'post',
        url: 'register',
        data: {
          username: this.user.name,
          password: this.user.pwd
        }
      }).then(successResponse => {
        if (successResponse.data.code === 200) {
          this.$notify({
            title: '成功',
            message: '注册成功！',
            type: 'success'
          })
          // TODO：跳转登录页
        } else {
          this.$notify.error({
            title: '错误',
            message: '注册失败！'
          })
        }
      }).catch(failResponse => {
        this.$notify.error({
          title: '错误',
          message: '注册失败！'
        })
      })
    }
  }
}
</script>

<style scoped>
.el-col {
  min-height: 1px;
}
#poster{
  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
  position: absolute;
  background: url("../../assets/Claude_Monet_038.jpg") no-repeat;
}
#login{
  width: 80%;
  margin-left: 50px;
}
</style>
