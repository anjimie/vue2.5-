<template>
  <div>
    <!-- http://img1.qunarzz.com/sight/p0/1501/d0/d00d72664c3e73d8.water.jpg_600x330_20d81a68.jpg -->
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImg" />
      <div class="banner-info">
        <div class="banner-tittle">
          {{this.sightName}}
        </div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe692;</span>
          {{this.bannerImgs.length}}
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallary
        :imgs="bannerImgs"
        v-show="showGallary"
        @close="handleGallaryClose"
      ></common-gallary>
    </fade-animation>
  </div>
</template>
<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  props:{
    sightName:String,
    bannerImg:String,
    bannerImgs:[]
  },
  data(){
    return {
      // //这里应该是请求过来的图片，但是之前讲过请求数据的方法了，这里暂时就先用静态的数组代替
      // imgs:['http://img1.qunarzz.com/sight/p0/1501/d0/d00d72664c3e73d8.water.jpg_600x330_20d81a68.jpg',
      //   'http://img1.qunarzz.com/sight/p0/201403/07/dca171d32e20adbf141e7f8f91b71c0e.jpg_r_800x800_f7e086d4.jpg'],
      gallaryClose: false 
    }
  },
  methods: {
    handleBannerClick (){
      this.gallaryClose = true; 
    },
    //CommonGallary画廊组件是一个公共组件（画廊为子组件，当前banner为父组件，父组件控制子组件的显示和隐藏）
    //想点击打开子组件，需要的过程是，点击banner中的图片，直接设置子组件的属性为true让子组件显示即可。
    //想点击关闭画廊组件，需要的过程是，点击子组件，让父组件切换子组件的属性为false，关闭子组件。
    //所以要想实现点击子组件关闭，子组件必须要用$emit(),传一个参数给父组件做通信。
    handleGallaryClose () {
      this.gallaryClose = false; 
    }
  },
  components: {
      CommonGallary
  }
}
</script>
<style lang='stylus' scoped>
  .banner
    position relative
    overflow hidden
    height 0
    padding-bottom 55%
    .banner-img
      width 100%
    .banner-info
      display flex
      position absolute
      left 0
      right 0
      bottom 0
      line-height .6rem
      color #fff
      background-image linear-gradient(top , rgba(0, 0, 0, 0), rgba(0, 0, 0, .8))
    .banner-title
      flex 1
      font-size .32rem
      padding 0 .2rem
    .banner-number
      height .32rem
      line-height .32rem
      margin-top .14rem
      padding 0 .4rem
      border-radius .4rem
      background rgba(0, 0, 0, .8)
      font-size .24rem
      .banner-icon
        font-size .24rem
</style>

