<template>
  <div class="imga">
    <h1>这是一个图片界面</h1>
    <el-row>
      <el-button>默认按钮</el-button>
      <el-button type="primary">主要按钮</el-button>
      <el-button type="success">成功按钮</el-button>
      <el-button type="info">信息按钮</el-button>
      <el-button type="warning">警告按钮</el-button>
      <el-button type="danger">危险按钮</el-button>
    </el-row>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .imga {
    /* min-height: 100vh; */
    display: flex;
    align-items: center;
  }
}
</style>