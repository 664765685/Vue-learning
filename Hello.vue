<template>
  <div>
    <group>
      <span>Vux输入框：</span><x-input class='red' title='邮箱' :is-type='be2333' @on-enter='onEnter'>
        <!-- <span slot='label'>邮箱</span> --> 
      </x-input>
    </group>
    <p>{{msgFromFather}}</p>
  </div>
</template>
<script>
  import {XInput} from 'vux'
  export default {
    components: {
      XInput
    },
    props: {
      msgFromFather: {
        type: String
      }
    },
    data: function () {
      return {
        inputValue: '',
        be2333: function (value) {
          return {
            valid: value === '2333',
            msg: 'Must be 2333'
          }
        }
      }
    },
    methods: {
      onEnter: function (value, $event) {
        alert(value)
        alert($event.target.name)
      },
      enter: function () {
        this.$emit('receive', this.inputValue)
      }
    }
  }
</script>
<style scoped>
  input{
    width: 300px;
  }
  p{
    margin: 10px auto;
    width: 200px;
    background-color: grey;
  }
  .red{
    width: 300px;
    margin: 10px auto;
    border: 1px solid black;
  }
</style>