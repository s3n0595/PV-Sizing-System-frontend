<template>
  <div class="container">
    <!-- 左侧内容 -->
    <div class="left">
      <!-- 引入createProject组件 -->
      <createProject  />
    </div>

    <!-- 右侧内容 -->
    <div class="right">
    <!--  引入googleMap组件-->
      <googleMap />
    </div>
  </div>
</template>

<script>
import createProject from '../left/createProject.vue'; // 引入 创建项目组件
import googleMap from "@/views/photovoltaic/right/googleMap.vue"; //引入  谷歌地图组建
export default {
  name: 'Layout',
  components: {
    createProject, // 注册 createProject 组件
    googleMap, //注册 谷歌地图组建
  },
};
</script>

<style scoped>
/* 容器样式 */
.container {
  display: flex;
  height: 90vh; /* 占满整个视口高度 */
}

/* 左侧样式 */
.left {
  width: 25%;
  background-color: #f0f0f0;
  padding: 20px;
  box-sizing: border-box;
}

/* 右侧样式 */
.right {
  width: 75%;
  background-color: #e0e0e0;
  padding: 2px;
  box-sizing: border-box;
}
</style>
