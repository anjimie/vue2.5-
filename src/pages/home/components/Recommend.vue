<template>
  <div>
      <div class="title">
          <span>
              <img  class="title-img" src="http://img1.qunarzz.com/piao/fusion/1711/89/ebc329f16c55bb02.png" alt="">
              </span>
          猜你喜欢</div>
      <ul>
          <!-- border-bottom1像素边框 -->
          <li class="item border-bottom" v-for="item of list" :key="item.id">
              <div class="item-img-wrapper">
                  <img class="item-img" :src="item.imgUrl" alt="">
              </div>
              <div class="item-info">
                  <p class="item-title">{{item.title}}</p>
                  <p class="item-desc">{{item.desc}}</p>
                  <button class="item-button">查看详情</button>
              </div>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props:{
      list:Array
  }
//   data() {
//       return {
//           recommendList:[{
//           id:'001',
//           imgUrl:'http://img1.qunarzz.com/sight/p0/1508/89/895a1b7add84f23faca053ce9e3153db.water.jpg_200x200_99ae30ee.jpg',
//           title:'北京欢乐谷',
//           desc:'亚洲唯一飞行式过山车等你来挑战'
//       },{
//           id:'002',
//           imgUrl:'http://img1.qunarzz.com/sight/p0/1508/89/895a1b7add84f23faca053ce9e3153db.water.jpg_200x200_99ae30ee.jpg',
//           title:'北京欢乐谷',
//           desc:'亚洲唯一飞行式过山车等你来挑战'
//       },{
//           id:'003',
//           imgUrl:'http://img1.qunarzz.com/sight/p0/1508/89/895a1b7add84f23faca053ce9e3153db.water.jpg_200x200_99ae30ee.jpg',
//           title:'北京欢乐谷',
//           desc:'亚洲唯一飞行式过山车等你来挑战'
//       },{
//           id:'004',
//           imgUrl:'http://img1.qunarzz.com/sight/p0/1508/89/895a1b7add84f23faca053ce9e3153db.water.jpg_200x200_99ae30ee.jpg',
//           title:'北京欢乐谷',
//           desc:'亚洲唯一飞行式过山车等你来挑战'
//       }]
//       }
//   }

}
</script>

<style lang="stylus" scoped>
@import '~styles/mixins.styl'
.title
    margin-top :.2rem
    line-height : .8rem
    background: #eee
    text-indent :.2rem
    .title-img
        width :.3rem
        height: .3rem
        padding-bottom :.1rem
.item   
    overflow :hidden
    display: flex
    height :1.9rem
    // background: red
    .item-img
        width :1.7rem
        height :1.7rem
        padding:.1rem
    .item-info
        flex:1 
        min-width :0
        padding:.1rem  
        .item-title
            line-height :.54rem
            font-size : .32rem 
            ellipsis()
        .item-desc
            line-height .4rem 
            color :#ccc
            ellipsis()
        .item-button
            line-height:.44rem 
            background #ff9300
            padding: 0 .2rem
            margin-top :.16rem
            border-radius : .06rem
            color :#fff
            


</style>
