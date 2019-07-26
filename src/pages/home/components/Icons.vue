<template>
    <div class="icons">
        <swiper :options="swiperOption">
            <!-- 从页面开始循环 -->
            <swiper-slide v-for="(page,index) of pages"  :key="index">
                <div class="icon"
                 v-for='item of page' :key='item.id'>
                    <div class="icon-img">
                        <img class="icon-img-content" :src="item.imgUrl" alt="">
                    </div>
                    <p class="icon-desc">{{item.desc}}</p>
                </div>
            </swiper-slide>     
        </swiper>  
    </div>
</template>

<script>
export default {
    name:'HomeIcons',
    props:{
        list :Array
    },
    data(){
        return {
            swiperOption:{
                autoplay:false
            }
        }
    },
    // data(){
    //     return {
    //         iconList:[{
    //             id :'0001',
    //             imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
    //             desc:'景点门票'
    //         },{
    //             id :'0002',
    //             imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png',
    //             desc:'故宫'                
    //         },{
    //             id :'0003',
    //             imgUrl:'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
    //             desc:'北京必游' 
    //         },{
    //             id :'0004',
    //             imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/3e/86314b2af03b7502.png',
    //             desc:'水上乐园'                 
    //         },{
    //             id :'0005',
    //             imgUrl:'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20191/0334cf5430b9b5505fd79e2b8d7e8670.png',
    //             desc:'爬长城'                 
    //         },{
    //             id :'0006',
    //             imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/67/9a1678221b8e0e02.png',
    //             desc:'古北水镇' 
    //         },{
    //             id :'0007',
    //             imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
    //             desc:'动植物园' 
    //         },{
    //             id :'0008',
    //             imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/fa/2548667cb6e902.png',
    //             desc:'北京野生动物园' 
    //         },{
    //             id :'0009',
    //             imgUrl:'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20194/b4511345827006994aa1980a3886f0ac.png',
    //             desc:'北京世园会' 
    //         },{
    //             id :'0010',
    //             imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/87/a6521252870ea402.png',
    //             desc:'考生专享'                 
    //         }]
    //     }
    // },
    // 实现分页,计算属性
    computed:{
        pages (){
            const pages=[]
            this.list.forEach((item,index)=>{
                const page = Math.floor(index/8)
                if(!pages[page]){
                    pages[page]=[]
                }
                pages[page].push(item)
            })
            return pages
        }
    }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
// 可以在下方左滑右滑
    .icons >>> .swiper-container
        // overflow :hidden
        // width :100%
        height :0
        padding-bottom :50%
        // background :green
    .icons 
        margin-top :.1rem
        .icon
            position :relative
            overflow :hidden
            float:left
            width :25%
            height:0
            padding-bottom :25%
            // background :red
            .icon-img
                position :absolute
                top:0
                left:0
                right:0
                bottom:.44rem
                box-sizing border-box
                padding : .1rem
                // background :blue
                .icon-img-content
                    display :block
                    margin : 0 auto
                    height:100%
            .icon-desc    
                position :absolute
                left:0
                right:0
                bottom:0rem
                height :.44rem
                line-height :.44rem
                color:$darkTextColor
                text-align :center
                // 过长省略,便于复用，转到了mixins.strl
                ellipsis()

                

</style>