<template>
<div id="app">
    <div class="loginbox">
        <div class="logo_container">
        <img src="../assets/logo.png" alt="">
        </div>
        <el-form ref='login_form_ref' label-width="80px" :model="form" class="form_login" :rules="login_rulers">
            <el-form-item  label="用户名" prop="user">
                <el-input v-model="form.user"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input  v-model='form.password' ></el-input>
            </el-form-item>
             <el-form-item class="button_file">
            <el-button type="primary" @click="login">登录</el-button>
            <el-button type="info" @click="resetloginform">a重置</el-button>
            </el-form-item>
        </el-form>
    </div>
</div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        user: '',
        password: ''
      },
      login_rulers: {
        user: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 3, max: 10, message: '用户名长度不对', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 6, max: 15, message: '密码长度不对', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    // resetloginform () {
    //   console.log(this.$refs)
    //   this.$refs.login_form_ref.resetFields()
    // }
    resetloginform: function () {
      console.log(this.$refs)
      this.$refs.login_form_ref.resetFields()
    },
    login: function () {
      console.log(this.$refs)
      this.$refs.login_form_ref.validate(val => {
        console.log(val)
        console.log(this)
        if (!val) return this.$message.error('登录失败')
        this.$message.success('登录成功')
      })
    }
    // resetloginform: () => {
    //   console.log(this.$refs)
    //   this.$refs.login_form_ref.resetFields()
    // }
  }
}

</script>

<style lang="css" scoped>
.loginbox{
width: 700px;
height: 400px;
position:absolute;
left: 50%;
top: 50%;
transform:translate(-50%,-70%);
background-color: #2e4e6e;
}
.logo_container {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    padding: 10px;
    background-color: #2f4f6f;
    position: absolute;
    left: 50%;
   transform:translate(-50%,-50%);
   box-shadow: 0 0 10px #ddd;

}
.logo_container img{
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: beige;
}
.form_login{
padding:0 20px;
width: 100%;
box-sizing: border-box;
position:absolute;
bottom: 50px;

}
.button_file{
display: flex;
justify-content: flex-end;

}
</style>
