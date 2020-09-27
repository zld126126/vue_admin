<template>
    <div id="login">
        <div class="login-wrap">
            <ul class="menu-tab">
                <li v-for="item in menuTabs" v-bind:key="item.id" v-bind:class="{'current':item.current}" @click="toggleMenu(item)">{{ item.txt}}</li>
            </ul>
            <!--表单start-->
            <el-form :model="ruleForm" status-icon :rules="rules" ref="ruleForm" class="login-form" size="medium">
                <el-form-item prop="pass" class="item-form">
                  <label class="left-label">邮箱</label>
                  <el-input type="password" v-model="ruleForm.pass" autocomplete="off"></el-input>
                </el-form-item>

                <el-form-item prop="checkPass" class="item-form">
                  <label class="left-label">密码</label>
                  <el-input type="password" v-model="ruleForm.checkPass" autocomplete="off"></el-input>
                </el-form-item>

                <el-form-item prop="age" class="item-form">
                  <label class="left-label">验证码</label>
                  <el-input v-model.number="ruleForm.age"></el-input>
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
        var checkAge = (rule, value, callback) => {
        if (!value) {
          return callback(new Error('年龄不能为空'));
        }
        setTimeout(() => {
          if (!Number.isInteger(value)) {
            callback(new Error('请输入数字值'));
          } else {
            if (value < 18) {
              callback(new Error('必须年满18岁'));
            } else {
              callback();
            }
          }
        }, 1000);
      };
      var validatePass = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请输入密码'));
        } else {
          if (this.ruleForm.checkPass !== '') {
            this.$refs.ruleForm.validateField('checkPass');
          }
          callback();
        }
      };
      var validatePass2 = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请再次输入密码'));
        } else if (value !== this.ruleForm.pass) {
          callback(new Error('两次输入密码不一致!'));
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
              pass: '',
              checkPass: '',
              age: ''
            },
            rules: {
              pass: [
                  { validator: validatePass, trigger: 'blur' }
              ],
              checkPass: [
                  { validator: validatePass2, trigger: 'blur' }
              ],
              age: [
                  { validator: checkAge, trigger: 'blur' }
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

.left-label {
  float: left;
}

</style>