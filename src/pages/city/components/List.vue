<template>
<!-- ref:获取dom -->
    <div class="list" ref="wrapper">
        <!-- better-scroll需要再有一层div -->
        <div>
            <div class="area">
                <div class="title border-topbottom">当前城市</div>
                <div class="button-list">
                    <div class="button-wrapper" v-for="item of hot" :key="item.id">
                        <div class="button">{{item.name}}</div> 
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button">北京</div> 
                    </div>
                </div>
            </div>
            <!-- 循环对象，所以第二项是key -->
            <div class="area" v-for="(item,key) of cities" :key="key">
                <div class="title border-topbottom">{{key}}</div>
                <div class="item-list">
                    <div class="item border-bottom"
                    v-for="innerItem of item" :key="innerItem.id">{{innerItem.name}}</div>
                </div>                                           
            </div>  
      </div>          
    </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
    name:'CityList',
    props:{
        cities:Object,
        hot:Array
    },
    mounted(){
        this.scroll = new BScroll(this.$refs.wrapper)
    }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.border-topbottom
    &:before
        border-color:#ccc
    &after 
        border-color:#ccc    
.border-bottom
    &:before
        border-color:#ccc  
//不能滚动    
.list
    overflow :hidden
    position :absolute
    top:1.58rem
    right:0
    left:0
    bottom :0
    // background :red
    .title
        line-height :.54rem
        background #eee
        padding-left:.2rem
        color:#666
        font-size :.24rem
    .button-list
        padding:.1rem  .6rem .1rem .1rem
        overflow :hidden
        .button-wrapper
            float: left
            width :33.33%
            .button
                margin :.1rem
                padidng:.1rem 0
                text-align :center
                border:.02rem solid #ccc
                border-radius:.06rem
    .item-list
        .item   
            line-height :.76rem
            // color :#666
            padding-left:.2rem


                

</style>