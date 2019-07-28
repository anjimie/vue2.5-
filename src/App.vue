<template>
  <div id="app">
    <keep-alive exclude='Detail'>
      <router-view/>
    </keep-alive>
    <!-- <keep-alive exclude='Detail'>   除了Detail组件其他都做缓存
      <router-view/>
    </keep-alive> -->
  </div>
</template>
<script>

export default {
  name: 'App'
}
</script>
// 10.11.164.70
// 真机测试兼容性问题：npm install babel-polyfill --save