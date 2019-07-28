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
