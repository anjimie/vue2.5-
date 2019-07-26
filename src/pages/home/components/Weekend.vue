<template>
  <div>
      <div class="title">
          周末去哪儿</div>
      <ul>
          <!-- border-bottom1像素边框 -->
          <li class="item border-bottom" v-for="item of recommendList" :key="item.id">
              <div class="item-img-wrapper">
                  <img class="item-img" :src="item.imgUrl" alt="">
              </div>
              <div class="item-info">
                  <p class="item-title">{{item.title}}</p>
                  <p class="item-desc">{{item.desc}}</p>
                  <!-- <button class="item-button">查看详情</button> -->
              </div>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  data() {
      return {
          recommendList:[{
          id:'001',
          imgUrl:'http://img1.qunarzz.com/sight/source/1811/f3/86173f863bef61.jpg_r_640x214_52b003ac.jpg',
          title:'京城周末撒欢',
          desc:'在帝都过周末，不仅仅是城中游！'
      },{
          id:'002',
          imgUrl:'http://img1.qunarzz.com/sight/source/1811/7e/476589267ebb41.jpg_r_640x214_bf599709.jpg',
          title:'京城溜娃必去',
          desc:'德智体美劳全面发展的亲子日，这些地方该去看看…'
      },{
          id:'003',
          imgUrl:'http://img1.qunarzz.com/sight/source/1505/aa/7baaf8a851d221.jpg_r_640x214_1431200f.jpg',
          title:'帝都必打卡',
          desc:'来北京必去的景点非这些地方莫属'
      },{
          id:'004',
          imgUrl:'http://img1.qunarzz.com/sight/source/1606/85/c6b6bad1b977e.jpg_r_640x214_5c638941.jpg',
          title:'漂流勇进，烧烤露营',
          desc:'轻松水上漂，任我乐逍遥'
      }]
      }
  }

}
</script>

<style lang="stylus" scoped>
@import '~styles/mixins.styl'
.title
    margin-top :.2rem
    line-height : .8rem
    background: #eee
    text-indent :.2rem
.item   
    // overflow :hidden
    // display: flex
    // height :1.9rem
    // // background: red
item-img-wrapper
    overflow :hidden
    hight :0
    padding-botton:33.9%
.item-img
    width :100%
    // height :1.7rem  
.item-info
    // flex:1 
    // min-width :0
    padding:.1rem  
    .item-title
        line-height :.54rem
        font-size : .32rem 
        color :#212121
        ellipsis()
    .item-desc
        line-height .4rem 
        color :#616161
        ellipsis()
    // .item-button
    //     line-height:.44rem 
    //     background #ff9300
    //     padding: 0 .2rem
    //     margin-top :.16rem
    //     border-radius : .06rem
    //     color :#fff
            


</style>
