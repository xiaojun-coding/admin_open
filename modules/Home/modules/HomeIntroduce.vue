<template>
  <el-col :span="12" class="Home-Introduce">
    <h2 class="Home-title">小鹿线后台管理框架</h2>
    <div class="Home-desc">
      Open-Deer（小鹿线基础权限框架）史上最精简的基础权限框架系统，完全开源、完全免费。公开解决了快速搭建展示型网站（如：企业官网、技术博客、信息门户等）的框架体系，是电子政务、电信综合门户、企业信息门户、知识管理平台、电子商务平台的基础性软件系统。可以帮助政府、企业或组织灵活、准确、高效、智能地管理信息内容，实现信息的采集、加工、审核、发布、存储、检索、统计、分析、
      反馈等整个信息生命周期的管理。采用时下最流行的Springboot+Vue3.0框架搭建开发，具有灵活小巧，配置简单，快速开发等特点。主要解决公司搭建网站成本高、投入大、周期长等问题，也可作为初创公司很好的基础技术框架。
    </div>
    <section class="line">
      <b>当前版本:</b>
      <span>v1.0.1</span>
      <el-tag type="danger" class="free">￥ 免费开源</el-tag>
    </section>
    <section class="line">
      <el-button type="primary" icon="MostlyCloudy" plain>
        <a href="https://gitee.com/opendeer/xiaoluxian_vue" target="_blank">
          访问码云
        </a>
      </el-button>

      <el-button icon="HomeFilled" plain>
        <a href="http://demo.open.xuexiluxian.cn" target="_blank"> 访问主页 </a>
      </el-button>
    </section>
  </el-col>
</template>

<script>
export default {
  data() {
    return {}
  }
}
</script>

<style lang="scss" scoped>
.Home-Introduce {
  background-color: #ffffff;
  .line {
    display: flex;
    align-items: center;
    padding-top: 14px;
    .free {
      margin-left: 12px;
    }
  }
  .Home-title {
    padding-bottom: 16px;
    font-size: 26px;
    font-weight: 100;
  }
  .Home-desc {
    line-height: 24px;
    text-align: justify;
  }
}
</style>
