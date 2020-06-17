<template>
  <el-container>
    <!-- 头部区域 -->
    <el-header>
      <div>
        <img src="../assets/shop.png" alt="">
        <span>菜鸟制作</span>
      </div>
      <el-button type="info" round @click="logout">退出</el-button>
    </el-header>
    <!-- 页面主体区域 -->
    <el-container>
      <!-- 侧边栏 -->
      <el-aside width="200px">
         <el-menu
      default-active="2"

      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b">
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-submenu index="1-4">
          <template slot="title">选项4</template>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      
    </el-menu>
      </el-aside>
        <!-- 右侧主要内容 -->
        <el-main>Main</el-main>

      </el-container>
    </el-container>

</template>

<script>
export default {
  data(){
    return{
      queryInfo:{
        query:'',
        pagenum: 1,
        pagesize: 2
      }
    }
  },
  created() {
    this.getMenuList();
  },
  methods: {
    logout() {
      // 清空token
      window.sessionStorage.clear()
      // 跳转到登录页
      this.$router.push('/login')
    },
    async getMenuList(){
      // const {data:res} = await this.$http.get('menu');
      const { data: res } = await this.$http.get('users',{params: this.queryInfo});
      
      console.log(res)
    }
  }
}
</script>

<style lang="less" scoped>
.el-container{
  height: 100%;
}
.el-header{
  background-color: #373d41;
  display: flex;
  justify-content: space-between;
  color: white;
  padding-left: 0px;
  div{
    display: flex;
    align-items: center;
    span{
      margin-left: 10px;
    }
  }
}

.el-aside{
  background-color: #333744;
}
.el-main{
  background-color: #fff;
}
</style>