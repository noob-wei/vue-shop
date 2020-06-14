<template>
  <div>
    <el-container class="home-container">
      <!-- 头部区域 -->
      <el-header>
        <div>
          <img src="../assets/shop.png" alt />
          <span>韦菜鸟大制作</span>
        </div>
        <el-button type="warning" round @click="logout">退出</el-button>
      </el-header>
      <!-- 页面主体区域 -->
      <el-container>
        <!-- 左侧侧边栏 -->
        <el-aside :width="isCollapse ? '64px' : '200px'" >
            <div class="toggle-button" @click="toggleCollapse">|||</div>
          <el-menu background-color="#545c64" text-color="#fff" active-text-color="#ffd04b" :unique-opened='true' :collapse='isCollapse' 
          :collapse-transition='false'>
            <el-submenu index="1">
              <template slot="title">
                <i class="el-icon-user-solid"></i>
                <span>用户管理</span>
              </template>
              <el-menu-item index="1-4-1">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>用户列表</span>
                </template>
              </el-menu-item>
            </el-submenu>

            <el-submenu index="2">
              <template slot="title">
                <i class="el-icon-view"></i>
                <span>权限管理</span>
              </template>
              <el-menu-item index="2-4-1">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>角色列表</span>
                </template>
              </el-menu-item>
              <el-menu-item index="2-4-2">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>权限列表</span>
                </template>
              </el-menu-item>
            </el-submenu>

            <el-submenu index="3">
              <template slot="title">
                <i class="el-icon-s-goods"></i>
                <span>商品管理</span>
              </template>
              <el-menu-item index="3-4-1">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>商品列表</span>
                </template>
              </el-menu-item>
              <el-menu-item index="3-4-2">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>分类参数</span>
                </template>
              </el-menu-item>
              <el-menu-item index="3-4-3">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>商品列表</span>
                </template>
              </el-menu-item>
            </el-submenu>
            
            <el-submenu index="4">
              <template slot="title">
                <i class="el-icon-upload"></i>
                <span>订单管理</span>
              </template>
              <el-menu-item index="4-4-1">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>商品列表</span>
                </template>
              </el-menu-item>
              <el-menu-item index="4-4-2">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>分类参数</span>
                </template>
              </el-menu-item>
              <el-menu-item index="4-4-3">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>商品列表</span>
                </template>
              </el-menu-item>
            </el-submenu>

            <el-submenu index="5">
              <template slot="title">
                <i class="el-icon-s-data"></i>
                <span>数据统计</span>
              </template>
              <el-menu-item index="5-4-1">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>商品列表</span>
                </template>
              </el-menu-item>
              <el-menu-item index="5-4-2">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>分类参数</span>
                </template>
              </el-menu-item>
              <el-menu-item index="5-4-3">
                <template slot="title">
                  <i class="el-icon-s-unfold"></i>
                  <span>商品列表</span>
                </template>
              </el-menu-item>
            </el-submenu>
          </el-menu>
        </el-aside>
        <!-- 右侧内容 -->
        <el-main>
            <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
    data() {
        return {
            // 是否折叠
            isCollapse: false
        }
    },
  methods: {
    logout() {
      // 清空token
      window.sessionStorage.clear()
      // 跳转到登录页
      this.$router.push('/login')
    },
    toggleCollapse() {
        this.isCollapse = !this.isCollapse
    }
  }
}
</script>

<style lang="less" scoped>
.home-container {
  height: 100vh;
}

.el-header {
  background-color: #373d41;
  display: flex;
  justify-content: space-between;
  padding-left: 0;
  color: #ffd04b;
  font-size: 1.5rem;
  align-items: center;
  div {
    display: flex;
    align-items: center;
  }
  span {
    margin-left: 10px;
  }
}

.el-aside {
  background-color: #373d41;
  span{
      margin-left: 10px;
  }
    .el-menu{
        border-right: none;
    }
}

.el-main {
  background-color: #ebeef5;
}

.toggle-button{
    background-color: rgb(44, 36, 36);
    color: #fff;
    text-align: center;
    letter-spacing: 0.2em;
    line-height: 24px;
    cursor: pointer;
    font-size: 10px;
}
</style>
