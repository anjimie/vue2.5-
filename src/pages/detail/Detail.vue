<template>
  <div>
    <detail-banner 
    :sightName="sightName"
    :bannerImg="bannerImg"
    :bannerImgs="gallaryImgs"
    ></detail-banner>
    <detail-header :list="list"></detail-header>
    
    <div class='content'>
      <detail-list :list="list"></detail-list>
       <!-- 此处景点详情内容不再赘述，开发用到的知识点之前都已经写过。 -->
    </div>
    
  </div>
</template>
<script>
import axios from 'axios'
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data(){
    return {
      sightName:'',
      bannerImg:'',
      gallaryImgs:[],
      list:[]
    }

  },
  methods: {
    getDetailInfo () {
      // 详情页数据交互，没有具体写，因为填充数据和之前的写法一样，所以把知识点讲一下就ok了。
      // 点击给地址传值的2种写法
      // axios.get('/api/detail.json?id='+ this.$route.params.id)
      axios.get('/api/detail.json?id=',{
        params:{
          id: this.$route.params.id
        }
      }).then(this.handleGetDataSucc)
    },
    handleGetDataSucc(res){
      res = res.data
      if(res.ret && res.data){
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg=data.bannerImg
        this.gallaryImgs =data.gallaryImgs
        this.list = data.categoryList
      }
      // console.log(res); 
    }
  },
  mounted () {
    this.getDetailInfo();
  },
  activated () { //解决进入页面的时候，由于缓存的原因，只加载一次数据的问题。也可以使用第二种方法，见App.vue
    this.getDetailInfo();
  }
}
</script>
<style lang='stylus' scoped>
  .content
    height 50rem
    padding-top 1rem
</style>


