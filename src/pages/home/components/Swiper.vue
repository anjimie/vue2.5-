<template>
<!-- 解决抖动感：加一个div标签 -->
    <div class="wrapper"> 
        <swiper :options="swiperOption">
            <!-- ref="mySwiper" @someSwiperEvent="callback" -->
            <!-- slides -->
            <swiper-slide v-for='item of swiperList' :key='item.id'>
                <img class="swiper-img" :src='item.imgUrl'>
            </swiper-slide>

            <!-- Optional controls -->
            <!-- 分页 -->
            <div class="swiper-pagination" slot="pagination"></div>
            <!-- 左右箭头 -->
            <!-- <div class="swiper-button-prev" slot="button-prev"></div>
            <div class="swiper-button-next" slot="button-next"></div> -->
            <!-- 进度条 -->
            <!-- <div class="swiper-scrollbar" slot="scrollbar"></div> -->
        </swiper>
    </div>
</template>
<script>
export default {
  name: 'HomeSwiper',
  data () {
      return {
        //   圆点的配置pagination
        // 图片循环loop
          swiperOption: {
              pagination:'.swiper-pagination',
              loop: true
              },
              swiperList:[{
                  id: '001',
                  imgUrl:'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20197/0b0622e5b6ac5fbed3084dd2832e6f8f.jpg_750x200_895321b6.jpg'
              },{
                  id:'002',
                  imgUrl:'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20197/c49de2c68e417f3de49f5d3d3b4c8d07.jpg_750x200_2f621cf4.jpg'
              }]
          }
  }
}
</script>
//  padding-bottom:31.25%：宽高比
// 或者：width:100%   height:31.25vm

<style lang="stylus" scoped>
// 圆点的颜色swiper-pagination-bullet swiper-pagination-bullet-active
.wrapper >>> .swiper-pagination-bullet-active
    background :#fff
.wrapper
    overflow : hidden
    width:100%
    height:0
    padding-bottom:26.67%
    background #eee
    .swiper-img
        width :100%

</style>
