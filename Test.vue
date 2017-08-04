<template>
<div>
  <hello @receive='valueUp' msg-from-father='"显示从父组件传入的值"'></Hello>
  <p>==== 显示子组件传递的数据 ====</p>
  <p>{{childMsg}}</p>
  <VInput title='邮箱' @checkEmail='checkEmail'>
    <span slot='right' v-if='captcha'><img src="../assets/captcha.png"></span>
    <span  class='warning' slot='warning' v-if='seen'>!</span>
    <button slot='button' @click='sendCaptcha'>发送验证码</button>
  </VInput>
</div>  
</template>
<script>
  import Hello from './Hello'
  import VInput from './Input'
  export default {
    data: function () {
      return {
        childMsg: '',
        captcha: false,
        seen: false
      }
    },
    components: {
      Hello,
      VInput
    },
    methods: {
      checkEmail: function (vValue) {
        var email = new RegExp('^([a-zA-Z0-9_-])+@([a-zA-Z0-9_-])+(.[a-zA-Z0-9_-])+')
        var temp = email.test(vValue)
        if (temp === true) {
          this.seen = false
        } else {
          this.seen = true
        }
      },
      valueUp: function (msg) {
        this.childMsg = msg
      },
      sendCaptcha: function () {
        this.captcha = !this.captcha
      }
    }
  }
</script>
<style scoped>
span.warning{
  display: inline-block;
  margin-top: -2px;
  margin-right: 10px;
  margin-left: 5px;
  border-radius: 50%;
  background-color: red;
  width: 20px;
  height: 20px;
  color: white;
}
span{
  display: table-cell;
  vertical-align: middle;
}
img{
/*   position: absolute;
  top: 12px; */
  margin-top: -3px;
  display: table-cell;
  vertical-align: center;
  width: 50px;
  height: 25px;
}
div{
  padding: 5px;
}
button{
  margin-top: -2px;
  margin-right: 10px;
  font-size: 16px;
}
</style>