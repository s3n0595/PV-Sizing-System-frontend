<template>
  <div class="container">
    <!-- 左侧内容 -->
    <div class="left">
      <!-- 引入createProject组件 -->
      <createProject  />
    </div>

    <!-- 右侧内容 -->
    <div class="right">
      <h2>右侧栏</h2>
      <p>这里是右侧内容，占 80%。</p>
    </div>
  </div>
</template>

<script>
import createProject from '../left/createProject.vue'; // 引入 创建项目组件
export default {
  name: 'Layout',
  components: {
    createProject, // 注册 createProject 组件
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
  padding: 20px;
  box-sizing: border-box;
}
</style>
