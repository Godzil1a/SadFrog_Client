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
              <el-menu-item index="5">
                <router-link to="/login">登录</router-link>
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
