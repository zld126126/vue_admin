<template>
    <div id="login">
        <div class="login-wrap">
            <ul class="menu-tab">
                <li v-for="item in menuTabs" v-bind:key="item.id" v-bind:class="{'current':item.current}" @click="toggleMenu(item)">{{ item.txt }}</li>
            </ul>
            <!--表单start-->
            <el-form :model="ruleForm" status-icon :rules="rules" ref="ruleForm" class="login-form" size="medium">
                <el-form-item prop="username" class="item-form">
                  <label>用户名</label>
                  <el-input v-model="ruleForm.username" autocomplete="off"></el-input>
                </el-form-item>

                <el-form-item prop="password" class="item-form">
                  <label>密码</label>
                  <el-input type="password" v-model="ruleForm.password" autocomplete="off" minlength="6" maxlength="24"></el-input>
                </el-form-item>

                <el-form-item prop="code" class="item-form">
                  <label>验证码</label>
                  <el-row :gutter="10">
                    <el-col :span="15"><el-input v-model.number="ruleForm.code" minlength="6" maxlength="6"></el-input></el-col>
                    <el-col :span="9"><el-button type="success">获取验证码</el-button></el-col>
                  </el-row>
                  
                </el-form-item>

                <el-form-item class="item-form">
                    <el-button type="danger" @click="submitForm('ruleForm')" class="login-btn block">提交</el-button>
                </el-form-item>
            </el-form>
            <!--表单end-->
        </div>
    </div>
</template>
<script>
export default {
    name: 'login',
    data(){
      // 验证码校验
      var validateCode = (rule, value, callback) => {
        let reg = /^[a-z0-9]{6}$/
        if (value === '') {
          callback(new Error('请输入验证码'));
        }else if (!reg.test(value)){
          callback(new Error('验证码格式有误'));
        }else {
          callback();
        }
      };
      // 用户名校验
      var validateUsername = (rule, value, callback) => {
        let reg = /^([a-zA-Z]|[0-9])(\w)+@[a-zA-Z0-9]+\.([a-zA-Z]{2,4})$/;
        if (value === '') {
          callback(new Error('请输入用户名'));
        }else if (!reg.test(value)){
          callback(new Error('用户名格式有误'));
        }else {
          callback();
        }
      };
      // 密码校验
      var validatePassword = (rule, value, callback) => {
        let reg = /^(?!\D+$)(?![^a-zA-Z]+$)\S{6,20}$/
        if (value === '') {
          callback(new Error('请输入密码'));
        }else if (!reg.test(value)){
          callback(new Error('密码格式有误'));
        } else {
          callback();
        }
      };
        return {
          menuTabs:[
            {txt:'登录',current:true},
            {txt:'注册',current:false}
          ],
          ruleForm: {
            username: '',
            checkPass: '',
            age: ''
          },
          rules: {
            username: [
                { validator: validateUsername, trigger: 'blur' }
            ],
            password: [
                { validator: validatePassword, trigger: 'blur' }
            ],
            code: [
                { validator: validateCode, trigger: 'blur' }
            ]
          }  
        };
    },
    created(){},
    mounted(){},
    methods:{
        toggleMenu(data){
          this.menuTabs.forEach(elem => {
              elem.current = false
          });
          data.current = true
        },

        submitForm(formName) {
          this.$refs[formName].validate((valid) => {
            if (valid) {
              alert('submit!');
            } else {
              console.log('error submit!!');
              return false;
            }
          });
        }
    },
    props:{},
    watch:{}
} 
</script>
<style lang="scss" scoped>
#login {
    height: 100vh;
    background-color: #344a5f;
}
.login-wrap {
    width: 330px;
    margin: auto;
}
.menu-tab {
    text-align: center;
    li {
        display: inline-block;
        width: 88px;
        line-height: 36px;
        font-size: 14px;
        color:white;
        border-radius: 2px;
        cursor: pointer;
    }
    .current {
        background-color: rgba(0,0,0,0.1);
    }
}
.login-form {
  margin-top: 29px;
  label {
    display: block;
    font-size: 14px;
    color: white;
    margin-bottom: 3px;
    text-align: left;
  }
  .item-form {
    margin-bottom: 13px;
  }
  .block {
    width: 100%;
    display: block;
  }
  .login-btn {
    margin-top: 19px;
  }
}
</style>