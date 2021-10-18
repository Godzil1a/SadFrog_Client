<template>
  <div class="hello">
    <el-container>
      <el-header>
        <el-row>
          <el-col :span="6">
            <img align="left" height="56" width="60" src="../assets/Sad_Frog.png">
          </el-col>
          <el-col :span="18">
            <el-menu :default-active="'1'" class="el-menu-demo" mode="horizontal">
              <el-menu-item index="1">首页</el-menu-item>
              <el-submenu index="2">
                <template slot="title">图书</template>
                <el-menu-item index="2-1">选项1</el-menu-item>
                <el-menu-item index="2-2">选项2</el-menu-item>
                <el-menu-item index="2-3">选项3</el-menu-item>
                <el-submenu index="2-4">
                  <template slot="title">选项4</template>
                  <el-menu-item index="2-4-1">选项1</el-menu-item>
                  <el-menu-item index="2-4-2">选项2</el-menu-item>
                  <el-menu-item index="2-4-3">选项3</el-menu-item>
                </el-submenu>
              </el-submenu>
              <el-menu-item index="3">音乐</el-menu-item>
              <el-menu-item index="4">
                个人管理
              </el-menu-item>
              <el-menu-item index="5" @click="loginVisible = true">
                登录
              </el-menu-item>
            </el-menu>
          </el-col>
        </el-row>
      </el-header>
      <el-main>
        <h1>
          陈静大吃屁
        </h1>
      </el-main>
    </el-container>
    <el-dialog
      title="登录"
      :visible.sync="loginVisible"
      width="30%">
      <el-row :gutter="20">
        <el-col :span="6">
          <div>用户名</div>
        </el-col>
        <el-col :span="18">
          <el-input v-model="userName" placeholder="请输入用户名"></el-input>
        </el-col>
      </el-row>
      <br>
      <el-row :gutter="20">
        <el-col :span="6">
          密码
        </el-col>
        <el-col :span="18">
          <el-input v-model="userPwd" placeholder="请输入密码" show-password></el-input>
        </el-col>
      </el-row>
      <span slot="footer" class="dialog-footer">
        <el-button @click="loginVisible = false">取消</el-button>
        <el-button type="primary" @click="login">登录</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      loginVisible: false,
      userName: '',
      userPwd: ''
    }
  },
  methods: {
    login () {
      this.$axios({
        method: 'post',
        url: 'login',
        data: {
          userName: this.userName,
          userPwd: this.userPwd
        }
      }).then(successResponse => {
        if (successResponse.data.code === 200) {
          this.$notify({
            title: '成功',
            message: '登录成功！',
            type: 'success'
          })
          this.loginVisible = false
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
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.el-menu-demo{
  border: none;
}
</style>
