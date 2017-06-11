<template>
  <div class="-experience">
    <div class="-title" v-text="expMsg.title"></div>
    <div class="-content">
      <div class="-banner" style="transform: rotateY(0deg) rotateX(0deg);">
        <div class="-experience-content">
          <div class="-left">
            <div class="-img" ></div>
          </div>
          <div class="-right" v-for="(exp,index) in expMsg.expList" v-if="index==curIndex">
            <h4 v-text="exp.title"></h4>
            <p class="-time" v-text="exp.time"></p>
            <p class="-post"><<span v-text="exp.post"></span>></p>
            <p class="-tech">"<span v-text="exp.tech"></span>"</p>
            <ul class="-list">
              <li class="-item"
                  v-for="item in exp.contentList" v-text="item">
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="-shout-cut">
        <ul class="-cut-list">
          <li class="-item" :class="{'-selected':index == curIndex}"
              v-for="(item, index) in curList"  @click="curIndex=index"></li>
        </ul>
      </div>
      <div class="-exp-des" v-text="expMsg.des"></div>
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        curList: [],
        curIndex: '0'
      }
    },
    props: ['expMsg']
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  @import '../stylus/cmpt.styl'
  .-experience{
    background: rgb(148, 92, 76) url(../img/bg.png);
    .-content{
      perspective:3000px;
      .-banner{
        width: 750px;
        height: 350px;
        background: #F2F4F5;
        margin:0 auto;
        border: 1px solid #eee;
        border-radius: 10px;
        color:#000;
        transition: transform .3s linear;
        overflow: hidden;
        box-shadow: 0 0 25px rgba(0,0,0,0.5);
        transform-style: preserve-3d;
        .-experience-content{
          transition: opacity 0.3s;
          height: 100%;
          .-left{
            float: left;
            height: 100%;
            position: relative;
            perspective: 800px;
            transform-style: preserve-3d;
            .-img{
              background: no-repeat center center;
              background-size: 55%;
              width: 150px;
              height: 100%;
              transform: translateZ(50px);
            }
            &:after{
              content: "";
              background: #eee;
              width: 1px;
              position: absolute;
              top: 10%;
              bottom: 10%;
              right: 0;
            }
          }
          .-right{
            padding-left: 50px;
            float: left;
            height: 100%;
            width: 550px;
            h4{
              color: #945C4C;
              font-size: 20px;
            }
            .-time{
              color: #AF7464;
              font-size: 14px;
            }
            .-post{
              color: #9E6351;
              font-size: 16px;
            }
            .-tech{
              color: #9E6351;
              font-size: 14px;
            }
            .-list{
              .-item{
                line-height: 30px;
                font-size: 16px;
                position: relative;
                &:before{
                  content: "";
                  position: absolute;
                  top: 50%;
                  left: -10px;
                  width: 5px;
                  height: 5px;
                  transform: translateY(-50%);
                  border-radius: 50%;
                  background-color: #AF7464;
                }
              }
              .-item-en{
                font-size: 14px;
              }
            }
          }
        }
      }
      .-shout-cut{
        width: 200px;
        margin: 0 auto;
        padding-top: 50px;
        .-cut-list{
          display: flex;
          justify-content: space-between;
          align-items: center;
          z-index: 101;
          .-item{
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background-color: #623C32;
            cursor:pointer;
            transition: background-color .3s linear;
            position: relative;
            &:before{
              content: '';
              position: absolute;
              top: -15px;
              right: -15px;
              left: -15px;
              bottom: -15px;
            }
          }
          .-selected{
            background-color: #AF7164;
          }
        }

      }
      .-exp-des{
        margin-top: 50px;
        color: #FFF;
        text-align: center;
        font-size: 18px;
      }
    }

  }

  @media screen and (max-width: 1366px) {
    .-experience {
      .-content {
        top: 150px;
        .-shout-cut{
          padding-top: 20px;
        }
        .-exp-des{
          margin-top: 20px;
        }
      }
    }
  }

  @media screen and (max-width: 600px){
    .-experience{
      .-content{
        top:80px;
        .-banner{
          width: 90%;
          height: 80%;
          .-experience-content{
            .-left{
              display: none;
            }
            .-right{
              width: 90%;
              margin: 0 auto;
              padding: 0;
              float: none;
              h4{
                font-size: 16px;
                margin: 10px 0;
              }
              p{
                margin: 10px 0;
              }
              .-time{
                font-size: 12px;
              }
              .-post{
                font-size: 14px;
              }
              .-tech{
                font-size: 13px;
              }
              .-list{
                .-item{
                  font-size: 12px;
                  line-height: 16px;
                  margin: 12px 0;
                }
              }
            }
          }
        }
        .-shout-cut{
          padding-top: 35px;
        }
        .-exp-des{
          display: none;
        }
      }
    }
  }
</style>
