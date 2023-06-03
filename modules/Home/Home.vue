<template>
  <SystemLayout>
    <div class="Home">
      <HomeHelper />
      <el-divider />

      <el-row>
        <HomeIntroduce />
        <HomeSelection />
      </el-row>

      <el-divider />
      <HomeFooter />
    </div>
  </SystemLayout>
</template>

<script>
import SystemLayout from "@modules/common/SystemLayout/SystemLayout.vue"
import HomeHelper from "./modules/HomeHeader.vue"
import HomeIntroduce from "./modules/HomeIntroduce.vue"
import HomeSelection from "./modules/HomeSelection.vue"
import HomeFooter from "./modules/HomeFooter.vue"
export default {
  components: {
    SystemLayout,
    HomeHelper,
    HomeIntroduce,
    HomeSelection,
    HomeFooter
  }
}
</script>

<style lang="scss" scoped>
.Home {
  min-height: calc(100% - 28px);
  padding: 1rem 1rem 2rem 1rem;
  font-size: 13px;
  color: #676a6c;
}
</style>
