<template>
<!-- 点击一个字母，跳转到对应的位置：兄弟组件传值：Alphabet传给city，再传给list -->
    <ul class="list">
        <!-- v-for="(item , key) of cities"  --> 
    <li
      class="item"
      v-for="item of letters"
      :key="item"
      :ref="item"
      @touchstart.prevent="handleTouchStart"
      @touchmove="handleTouchMove"
      @touchend="handleTouchEnd"
      @click="handleLetterClick"
    >
        {{item}}
        </li>
    </ul>
</template>

<script>
export default {
    name:'CityAlphabet',
    props:{
        cities:Object
    },
    computed: {
        letters(){
            const letters = []
            for(let i in this.cities){
                letters.push(i)
            }
            console.log(letters)
            return letters
        }
    },
    data(){
        return {
            touchStatus:false,
            startY : 0,
            // 函数节流
            timer: null
        }
    },
    // 页面完成渲染之后
    updated(){
        this.startY = this.$refs['A'][0].offsetTop
    },
    methods:{
        handleLetterClick(e){
            // console.log(e.target.innerText)
            this.$emit('change',e.target.innerText)

        },
        handleTouchStart(){
            this.touchStatus = true
        },
        // 在右边的字母处移动时，城市也会变
        handleTouchMove(e){
            if(this.touchStatus){
                if(this.timer){
                    clearTimeout(this.timer)
                }
                // 16毫秒
                this.timer = setTimeout(() => {
                    // 获取A元素距离顶部的高度
                    // const startY = this.$refs['A'][0].offsetTop
                    const touchY = e.touches[0].clientY - 79
                    // 除以每个字母的高度
                    const index = Math.floor((touchY - this.startY) / 20)
                    if(index >= 0 && index <= this.letters.length){
                        this.$emit('change',this.letters[index])
                    }
                },16)
                
            }

        },
        handleTouchEnd(){
            this.touchStatus = false

        }
    }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.list
    display:flex
    flex-direction :column
    justify-content :center
    position :absolute
    top:1.58rem
    right:0
    bottom:0
    width:.4rem
    // background:red
    .item
        text-align :center
        line-height :.4rem
        color:$bgColor
</style>