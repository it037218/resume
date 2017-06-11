<template>
  <div id="app">
    <r-header v-on:showPage="changeShowItem"></r-header>
    <r-main :idx="msg"></r-main>
    <r-footer v-if="msg==5"></r-footer>
  </div>
</template>

<script>
  import rHeader from './components/rHeader'
  import rMain from './components/rMain'
  import rFooter from './components/rFooter'

  export default {
    name: 'app',
    components: {
      rHeader,
      rMain,
      rFooter
    },
    data () {
      return {
        msg: 0
      }
    },
    methods: {
      changeShowItem (idx) {
        this.msg = idx
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus">
  body{
    font-family: "Helvetica Neue", Helvetica, Arial, "PingFang SC", "Hiragino Sans GB", "Heiti SC", "Microsoft YaHei", "WenQuanYi Micro Hei", sans-serif;
    margin: 0;
  }

  ul,li{
    list-style: none;
    margin: 0;
    padding: 0;
  }
  a{
    color: #000;
    text-decoration: none;
    &:hover{
      color: #000;
    }
    &:link{
      color: #000;
    }
  }
</style>>
