<template>
  <div class="-default">
    <div class="-content">
      <div class="-photo"></div>
      <div class="-des">
        <p class="-quote" v-text="defMsg.quote"></p>
        <div class="-des-list">
          <p v-for="item in defMsg.desList" v-text="item"></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        info: {}
      }
    },
    props: ['defMsg']
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  @import '../stylus/cmpt.styl'
  .-default{
    background: rgb(135, 176, 165) url("../img/bg.png");
    .-content{
      top: 200px;
    }
    .-photo{
      width: 150px;
      height: 150px;
      border-radius: 50%;
      background: url("../img/timg1.jpg") no-repeat center center;
      background-size: contain;
      margin: 0 auto;
      transition: box-shadow .5s linear;
      &:hover{
        box-shadow: 0 0 15px #1FAEFF;
      }
    }
    .-des{
      text-align: center;
      max-width: 90%;
      margin: 0 auto;
      color: #FFF;
      .-quote{
        font-size: 22px;
        position: relative;
        padding: 20px 0;
        &:after{
          content: "";
          position: absolute;
          left: 10%;
          right: 10%;
          bottom: 0;
          height: 1px;
          background-color: rgba(255,255,255,0.6);
        }
      }
      .-des-list{
        padding-top: 20px;
        line-height: 20px;
        font-size: 18px;
        p{
          margin: 24px 0;
        }
      }
    }
  }


  @media screen and (max-width: 1366px){
    .-default {
      .-content {
        top: 120px;
      }
    }
  }

  @media screen and (max-width: 600px){
    .-default {
      .-content {
        top: 80px;
      }
      .-des{
        .-quote{
          font-size: 16px;
        }
        .-des-list{
          padding: 0;
          line-height: 16px;
          font-size: 14px;
          p{
            margin: 20px 0;
          }
        }
      }
    }
    .-title{
      display: none;
    }
  }
</style>
