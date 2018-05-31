<template>
  <div class="login-form">
    <div class="form-line">
      <span class="form-label">用户名：</span>
      <div class="form-input">
        <input type="text" v-model="userName" placeholder="请填入用户名">
      </div>
      <span class="form-error">{{userNameError.errorText}}</span>
    </div>
    <div class="form-line">
      <span class="form-label">密码：</span>
      <div class="form-input">
        <input type="password" v-model="userPwd" placeholder="请填入密码">
      </div>
      <span class="form-error"></span>
    </div>
    <div class="form-line">
      <span class="form-label"></span>
      <div class="form-btn">
        <button>登录</button>
      </div>
    </div>
    <span>登录失败</span>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        userName: '',
        userPwd: ''
      }
    },
    computed: {
      userNameError() {
        let errorText,status
        if(!/@/.test(this.userName)){
          status=false
          errorText='用户名必须包含@'
        }else{
          status=true
          errorText=''
        }
        if(!this.userFlag){
          errorText=''
          this.userFlag=true
        }
        return {status,errorText}
      }
    },
  }
</script>

<style lang='less' scoped>
  .form-line{
    padding: 15px 0;
    .form-label{
      display: inline-block;
      width: 100px;
      font-size: 16px;
    }
    .form-input{
      display: inline-block;
      input{
        height: 30px;
        width: 300px;
        line-height: 30px;
        text-indent:5px;
        border: 1px solid #ccc;
      }
    }
    .form-btn{
      display: inline-block;
      button{
        padding: 10px 20px;
        background-color: #4fc08d;
        color: #fff;
        border: 0 none;
        cursor: pointer;
      }
    }
    .form-error{
      color: red;
    }
  }
</style>