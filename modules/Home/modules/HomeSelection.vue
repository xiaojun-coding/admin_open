<template>
  <el-col :span="12" class="Home-Selection">
    <h2 class="Home-title">技术选型</h2>
    <el-row>
      <el-col :span="12">
        <h4>后端技术</h4>
        <ul class="technology">
          <li><el-tag>Spring Boot 2</el-tag></li>
          <li><el-tag>Spring Security 5.6.3</el-tag></li>
          <li><el-tag>Hutool 5.8.0</el-tag></li>
          <li><el-tag>MyBatis-Plus 3.5.1</el-tag></li>
          <li><el-tag>Logback</el-tag></li>
          <li><el-tag>....</el-tag></li>
        </ul>
      </el-col>
      <el-col :span="12">
        <h4>前端技术</h4>
        <ul class="technology">
          <li><el-tag>Vue3</el-tag></li>
          <li><el-tag>Vue-Router</el-tag></li>
          <li><el-tag>Pinia</el-tag></li>
          <li><el-tag>Element-Plus</el-tag></li>
          <li><el-tag>Axios</el-tag></li>
          <li><el-tag>Wangeditor</el-tag></li>
          <li><el-tag>Crypto.js</el-tag></li>
          <li><el-tag>Echarts</el-tag></li>
          <li><el-tag>....</el-tag></li>
        </ul>
      </el-col>
    </el-row>
  </el-col>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.Home-Selection {
  background-color: #ffffff;
  padding-left: 50px;
  h2 {
    padding-bottom: 16px;
    font-size: 26px;
    font-weight: 100;
  }
  h4 {
    font-weight: 500;
    padding-bottom: 14px;
  }
  .technology {
    li {
      padding: 4px 0;
    }
  }
}
</style>
