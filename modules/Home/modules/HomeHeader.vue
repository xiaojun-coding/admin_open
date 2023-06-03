<template>
  <el-alert :title="title" type="success" :closable="false">
    {{ nowTime }}
  </el-alert>
</template>

<script>
import { formatStamp } from "@share/helper/formatDate"
import { useGlobalUserStore } from "@store/UserGlobalStore"
import { mapState } from "pinia"
export default {
  data() {
    return {
      nowTime: ""
    }
  },
  computed: {
    ...mapState(useGlobalUserStore, ["userInfo"]),
    title() {
      const username = this.userInfo ? this.userInfo.username : ""
      return `${username} 欢迎回来小鹿线基础框架！`
    }
  },
  methods: {
    init() {
      this.setNowTime()
    },
    setNowTime() {
      this.timer = setInterval(() => {
        this.nowTime = formatStamp("YYYY年MM月DD日 HH时MM分SS秒")
      }, 1000)
    }
  },
  created() {
    this.init()
  },
  unmounted() {
    clearInterval(this.timer)
  }
}
</script>

<style lang="scss" scoped>
:deep(.el-alert__content) {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 0;
}
</style>
