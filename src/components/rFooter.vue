<template>
  <div class="-footer">
    <p v-for="item in contentList" v-text="item"></p>
  </div>
</template>

<script>
  export default{
    data () {
      return {
        contentList: []
      }
    },
    mounted: function () {
      this.$nextTick(function () {
        this.dataView()
      })
    },
    methods: {
      dataView: function () {
        let _this = this
        this.$http.get('/api/footer').then(function (res) {
          if (res.data.errno === 0) {
            _this.contentList = res.data.footer.contentList
          }
        })
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .-footer{
    position: absolute;
    z-index: 10;
    left: 0;
    right: 0;
    bottom: 0;
    border-top: 1px solid #756D4D;
    text-align: center;
    color: #756D4D;
    p{
      margin: 5px 0;
      font-size: 12px;
    }
  }
</style>
