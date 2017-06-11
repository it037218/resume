<template>
  <div class="-contact">
    <div class="-title" v-text="contMsg.title"></div>
    <div class="-content" >
      <div class="-contact-des1">
        <span v-for="item in contMsg.desList1" v-text="item"></span>
      </div>
      <div class="-contact-des2">
        <p v-for="item in contMsg.desList2" v-text="item"></p>
      </div>
      <!--<div class="-contact-download">-->
      <!--<div class="-download-title">{{$ctrl.download}}</div>-->
      <!--<div class="-download-list">-->
      <!--<a href="{{item.url}}" target="_blank" ng-repeat="item in $ctrl.fileList track by $index">{{item.title}}</a>-->
      <!--</div>-->
      <!--</div>-->
      <div class="-contact-type">
        <a class="-item" v-for="item in contMsg.typeList" :href="item.url" target="_blank">
          <img :src="item.icon" alt="">
        </a>
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
    props: {
      contMsg: Object
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  @import '../stylus/cmpt.styl'
  .-contact{
    color:#FFF;
    background: rgb(162, 153, 113) url("../img/bg.png");
    .-content{
      max-width: 300px;
      margin: 0 auto;
      text-align: center;
      .-contact-des1{
        font-size: 22px;
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
        span:nth-child(1){
          color:#F00;
        }
        span:nth-child(2){
          color:#3cf;
        }
        span:nth-child(3){
          color:#6c0;
        }
        span:nth-child(4){
          color:#f63;
        }
      }
      .-contact-des2{
        font-size: 18px;
      }
      .-contact-download{
        margin-top: 50px;
        color: #59543A;
        .-download-title{
          font-size: 17px;
        }
        .-download-list{
          display: flex;
          justify-content: space-between;
          max-width: 180px;
          margin: 0 auto;
          padding-top: 20px;
          a{
            display: inline-block;
            color:#59543A;
            border: 1px solid #888059;
            border-radius: 5px;
            padding: 5px;
            width: 60px;
            font-size: 12px;

            position: relative;
            -webkit-tap-highlight-color: transparent;
            transform: translateZ(0);
            box-shadow: 0 0 1px transparent;

            &:before,&:after{
              content: '';
              position: absolute;
              left: 0;
              width: 100%;
              height: 5px;
              opacity: 0;
              transition: opacity 0.3s;
            }
            &:before{
              bottom: 100%;
              background: radial-gradient(ellipse at 50% 150%, rgba(105, 100, 68, 0.6) 0%, rgba(105, 100, 68, 0) 80%);
            }
            &:after{
              top: 100%;
              background: radial-gradient(ellipse at 50% -50%, rgba(105, 100, 68, 0.6) 0%, rgba(105, 100, 68, 0) 80%);
            }
            &:hover:before,&:hover:after{
              opacity: 1;
            }

          }
        }
      }
      .-contact-type{
        display: flex;
        justify-content: space-around;
        margin: 100px auto 0;
        .-item{
          border-radius: 50%;
          border: 1px solid #FFF;
          width: 40px;
          height: 40px;
          position: relative;
          img{
            width: 65%;
            position: absolute;
            top: 50%;
            right: 50%;
            transform: translateX(50%) translateY(-50%);
          }
        }
      }
    }
    .-content-en{
      max-width: 400px;
      .-contact-des2{
        font-size: 15px;
      }
      .-contact-type{
        width: 80%;
      }
    }


  }
  @media screen and (max-width: 1366px) {
    .-contact {
      .-content {
        top: 150px;
      }
    }
  }


  @media screen and (max-width: 600px){
    .-contact{
      .-content{
        top:80px;
        max-width: 250px;
        .-contact-des1{
          font-size: 18px;
        }
        .-contact-des1-en{
          font-size: 16px;
        }
        .-contact-des2{
          font-size: 15px;
        }
        .-contact-download{
          .-download-title{
            font-size: 16px;
          }
        }
        .-contact-type{
          margin: 50px auto 0;
          width: 90%;
          .-item{
            width: 30px;
            height: 30px;
          }
        }
      }
      .-content-en{
        max-width: 300px;
        .-contact-des2{
          font-size: 14px;
        }
      }
    }
  }
  @media screen and (max-height: 470px){
    .-contact{
      .-content {
        .-contact-des2{
          font-size: 14px;
        }
        .-contact-download{
          margin-top: 20px;
        }
      }
    }
  }
</style>
