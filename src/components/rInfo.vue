<template>
  <div class="-info">
    <div class="-title" v-text="infoMsg.title"></div>
    <div class="-content">
      <div>
        <ul class="-info-list">
          <li class="-info-item" v-for="item in infoMsg.infoList">
            <div class="-cont">
              <div class="-img">
                <img :src="item.icon" alt="">
              </div>
              <div class="-intro">
                <span v-text="item.key"></span>/<span v-text="item.value"></span>
              </div>
            </div>
          </li>
        </ul>
      </div>
      <div class="-info-des">
        <p v-for="item in infoMsg.desList" v-text="item"></p>
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
    props: ['infoMsg']
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  @import '../stylus/cmpt.styl'
  .-info{
    background: rgb(16, 144, 133) url(../img/bg.png);
    .-info-list{
      max-width: 800px;
      margin: 0 auto;
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      font-size: 18px;
      .-info-item{
        width: 100px;
        margin: 0 20px;
        .-cont{
          .-img{
            width: 90px;
            height: 90px;
            cursor: pointer;
            transition: transform ease-out 0.1s, background 0.2s;
            background: rgba(255,255,255,0.1);
            border-radius: 50%;
            position: relative;
            margin: 0 auto;
            img{
              width: 50%;
              position: absolute;
              top: 50%;
              right: 50%;
              transform: translateY(-50%) translateX(50%);
            }
            &:after{
              content: '';
              position: absolute;
              box-shadow: 0 0 0 2px rgba(255,255,255,0.1);
              opacity: 0;
              transform: scale(0.9);
              width: 100%;
              height: 100%;
              border-radius: 50%;
            }
            &:hover{
              background: rgba(255,255,255,0.05);
              transform: scale(0.93);
              color: #fff;
            }
            &:hover:after{
              animation: effect 1.3s ease-out 75ms;
            }
          }
          .-intro{
            text-align: center;
            margin-top: 20px;
            color: #FFF;
          }
          .-intro-en{
            width: 150px;
            position: relative;
            left: -25px;
          }
        }
      }
    }
    .-info-des{
      text-align: center;
      line-height: 24px;
      padding-top: 50px;
      font-size: 18px;
      color: #FFF;
    }
  }

  @keyframes effect {
    0% {
      opacity: 0.3;
    }
    40% {
      opacity: 0.5;
      box-shadow: 0 0 0 2px rgba(255,255,255,0.1), 0 0 10px 10px #109085, 0 0 0 10px rgba(255,255,255,0.5);
    }
    100% {
      box-shadow: 0 0 0 2px rgba(255,255,255,0.1), 0 0 10px 10px #109085, 0 0 0 10px rgba(255,255,255,0.5);
      transform: scale(1.5);
      opacity: 0;
    }
  }

  @media screen and (max-width: 1366px) {
    .-info {
      .-content {
        top: 160px;
      }
    }
  }

  @media screen and (max-width: 600px){
    .-info {
      .-content{
        top: 80px;
        .-info-list{
          .-info-item{
            .-cont{
              .-img{
                width: 50px;
                height: 50px;
              }
            }
            .-intro{
              margin: 20px 0;
              font-size: 12px;
            }
          }
        }
        .-info-des{
          padding-top: 15px;
          line-height: 16px;
          font-size: 14px;
        }
        .-info-des-en{
          font-size: 12px;
          width: 95%;
          margin: 0 auto;
        }
      }
    }
    .-title{
      display: none;
    }
  }
  @media screen and (max-height: 550px){
    .-info{
      .-content {
        .-info-des-en{
          padding-top: 0;
          font-size: 12px;
          width: 95%;
          margin: 0 auto;
          p{
            margin: 5px 0;
          }
        }
      }
    }
  }
</style>
