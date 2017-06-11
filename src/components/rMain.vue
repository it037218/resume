<template>
  <div class="dock-fill" ref="main-wrap">
    <r-default class="page-section" :class="{'cur-page': idx == 0,'prev-page': idx==1}"
               :def-msg="parentDefMsg"></r-default>

    <r-info class="page-section" :class="{'cur-page': idx == 1,'prev-page': idx==2,'next-page': idx==0}"
            :info-msg="parentInfoMsg"></r-info>

    <r-skill class="page-section" :class="{'cur-page': idx == 2,'prev-page': idx==3,'next-page': idx==1}"
             :skill-msg="parentSkillMsg"></r-skill>

    <r-experience class="page-section" :class="{'cur-page': idx == 3,'prev-page': idx==4,'next-page': idx==2}"
                  :exp-msg="parentExperienceMsg"></r-experience>

    <r-works class="page-section" :class="{'cur-page': idx == 4,'prev-page': idx==5,'next-page': idx==3}"
             :works-msg="parentWorksMsg"></r-works>

    <r-contact class="page-section" :class="{'cur-page': idx == 5,'next-page': idx==4}"
               :cont-msg="parentContMsg"></r-contact>

    <div class="-arrow" style="display: block;"></div>

  </div>
</template>

<script>
  import rDefault from '@/components/rDefault'
  import rInfo from '@/components/rInfo'
  import rContact from '@/components/rContact'
  import rSkill from '@/components/rSkill'
  import rExperience from '@/components/rExperience'
  import rWorks from '@/components/rWorks'
  export default{
    name: 'rMain',
    components: {
      rDefault,
      rInfo,
      rSkill,
      rExperience,
      rWorks,
      rContact
    },
    data () {
      return {
        parentDefMsg: {},
        parentInfoMsg: {},
        parentSkillMsg: {},
        parentExperienceMsg: {},
        parentWorksMsg: {},
        parentContMsg: {}
      }
    },
    props: ['idx'],
    mounted: function () {
      this.$nextTick(function () {
        this.infoView()
      })
    },
    methods: {
      infoView: function () {
        let _this = this
        this.$http.get('/api/mainbody').then(function (res) {
          if (res.data.errno === 0) {
            _this.parentDefMsg = res.data.mainbody.default
            _this.parentInfoMsg = res.data.mainbody.info
            _this.parentSkillMsg = res.data.mainbody.skill
            _this.parentExperienceMsg = res.data.mainbody.experience
            _this.parentWorksMsg = res.data.mainbody.works
            _this.parentContMsg = res.data.mainbody.contact
          }
        })
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .dock-fill, .page-section {
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    overflow: hidden;
    position: absolute;
  }

  .dock-fill {
    background: #eee;
  }

  .page-section {
    display: none;
  }

  .active, .cur-page, .next-page, .prev-page {
    display: block;
  }

  .active {
    -webkit-transition: -webkit-transform .5s;
    transition: -webkit-transform .5s;
    transition: transform .5s;
    -webkit-transform: translateY(0) !important;
    transform: translateY(0) !important;
    z-index: 100;
  }

  .cur-page {
    z-index: 10;
  }

  .prev-page {
    -webkit-transform: translateY(-100%);
    transform: translateY(-100%);
  }

  .next-page {
    -webkit-transform: translateY(100%);
    transform: translateY(100%);
  }

  .-arrow {
    position: absolute;
    bottom: 20px;
    width: 20px;
    height: 35px;
    left: 50%;
    z-index: 100;
    background: url(../img/arrow.svg) bottom center no-repeat;
    background-size: contain;
    pointer-events: none;
    -webkit-transform: translateX(-50%);
    transform: translateX(-50%);
    -webkit-animation: arrowAnimate 1.5s ease-in-out infinite;
    animation: arrowAnimate 1.5s ease-in-out infinite;
  }

  @keyframes arrowAnimate {
    0% {
      bottom: 10px;
      opacity: .8;
    }
    50% {
      bottom: 20px;
      opacity: 1;
    }
    80% {
      bottom: 22px;
      opacity: .4;
    }
    100% {
      bottom: 22px;
      opacity: 0;
    }
  }

</style>

