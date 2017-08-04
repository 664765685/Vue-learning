<template>
<div>
  <div class="outDiv">
  <span>{{title}}</span>
  <input type="" name="" @keydown='show' v-model='vValue'>
  <button :style='{visibility: seen}' @click='onDelete' class='delete'>X</button>
  <slot name='right'></slot>
  <slot name='warning'></slot>
  <slot name='button'></slot>
  </div>
</div>
</template>
<script>
  export default {
    props: {
      title: {
        type: String
      }
    },
    data: function () {
      return {
        vValue: '',
        seen: 'hidden'
      }
    },
    methods: {
      show: function () {
        if (this.vValue === '') {
          this.seen = 'hidden'
        } else {
          this.seen = 'visible'
        }
        this.$emit('checkEmail', this.vValue)
      },
      onDelete: function () {
        this.vValue = ''
        this.seen = 'hidden'
      }
    }
  }
</script>
<style scoped>
  button.delete{
    border: 0;
    color: white;
  }
  span{
    display: inline-block;
    width: 70px;
    word-wrap: break-word;
  }
  .outDiv{
    display: inline-block;
    position: relative;
    border: 1px solid black;
    margin: 20px auto;
  }
  input{
    font-size: 16px;
    height: 45px;
    border: 0;
    outline: 0;
    display: inline-block;
  }
</style>