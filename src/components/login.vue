<template>
  <div class="login_container">
    <div class="login-box">
      <!-- 头像区域 -->
      <div class="avatar_box">
        <img src="../assets/12.png" />
      </div>

      <!-- 登录表单区域 -->
      <el-form
        ref="loginFormRef"
        :model="loginForm"
        :rules="loginFormRules"
        label-width="0px"
        class="login_form"
      >
        <!-- 用户名 -->
        <el-form-item prop="username">
          <el-input v-model="loginForm.username" placeholder="用户名" prefix-icon="el-icon-s-custom"></el-input>
        </el-form-item>
        <!-- 密码 -->
        <el-form-item prop="password">
          <el-input
            v-model="loginForm.password"
            placeholder="密码"
            prefix-icon="el-icon-lock"
            type="password"
          ></el-input>
        </el-form-item>
        <!-- 按钮 -->
        <el-form-item class="btns">
          <el-button type="primary" round @click="login">登录</el-button>
          <el-button type="info" round @click="resetLoginForm">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 登录表绑定的数据对象
      loginForm: {
        username: 'admin',
        password: '123456'
      },
      loginFormRules: {
        // 表单的验证规则对象
        // 验证用户名是否合法
        username: [
          // 参数：1，规则：
          // required：是否为必填项  min，max：长度范围
          // 2，错误的消息message，当不符合规则时触发
          // 3.什么行为时触发这个规则 trigger：‘blur’：鼠标失去焦点手机

          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur' }
        ],
        // 验证密码是否合法
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { min: 6, max: 12, message: '长度在 6 到 12 个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    resetLoginForm() {
      this.$refs.loginFormRef.resetFields()
    },
    login() {
      this.$refs.loginFormRef.validate(async valid => {
        // console.log(valid);//ture / false
        const result = await this.$http.post('login', this.loginForm)
        // console.log(result.data)
        if (result.data.meta.status !== 200)
          return this.$message.error('登录失败了哦~')
        this.$message.success('登录成功！！！')

        window.sessionStorage.setItem('token', result.data.token)
        // 通过编程式导航跳转到后台主页，路由地址是 /home
        this.$router.push('/home')
      })
    }
  }
}
</script>

<style lang="less" scoped>
.login_container {
  background-color: #2b4b6b;
  height: 100%;
}
.login-box {
  width: 450px;
  height: 300px;
  background-color: #fff;
  border-radius: 5px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
.avatar_box {
  width: 100px;
  height: 100px;
  border: 1px solid #eee;
  border-radius: 50%;
  box-shadow: 0 0 10px gray;
  padding: 5px;
  position: absolute;
  left: 50%;
  transform: translate(-50%, -50%);
  img {
    width: 100%;
    height: 100%;
    border-radius: 50%;
  }
}

.login_form {
  position: absolute;
  bottom: 0;
  width: 100%;
  padding: 0 20px;
  box-sizing: border-box;
}

.btns {
  display: flex;
  justify-content: flex-end;
}
</style>
