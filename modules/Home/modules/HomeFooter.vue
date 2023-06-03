<template>
  <div class="HomeFooter">
    <el-card class="box-card">
      <template #header>
        <div class="card-header">联系方式</div>
      </template>

      <template #default>
        <div class="contact">
          <section class="contact-item">
            <el-icon><Promotion /></el-icon>
            <span class="title">官网</span>
            <div class="contact-information">
              <el-link
                :underline="false"
                href="http://open.xuexiluxian.cn"
                target="_blank"
              >
                http://open.xuexiluxian.cn
              </el-link>
            </div>
          </section>
          <section class="contact-item">
            <el-icon><UserFilled /></el-icon>
            <span class="title">QQ群</span>
            <div class="contact-information">
              <el-link
                :underline="false"
                target="_blank"
                href="https://qm.qq.com/cgi-bin/qm/qr?k=5qn-R4GtfmjsOkbduG5VaAr2TQu3NGLa&jump_from=webapi"
                >530344089</el-link
              >
            </div>
          </section>
          <section class="contact-item">
            <IconWx />
            <span class="title">微信</span>
            <div class="contact-information">
              <span>iteachyou2020, </span>
              <span>zqx13949660512, </span>
              <span>XiAoWang-1016</span>
            </div>
          </section>
          <section class="contact-item">
            <IconQq />
            <span class="title">QQ</span>
            <div class="contact-information">
              <span>153095904,</span>
              <span>2591356063</span>
            </div>
          </section>
        </div>
      </template>
    </el-card>

    <el-card class="box-card">
      <template #header>
        <div class="card-header">更新日志</div>
      </template>
      <template #default>
        <el-scrollbar height="200px">
          <div class="journal">
            <div class="journal-item">
              <span>v1.0.1 - 2022-08-03</span>
              <el-link :underline="false" type="primary" @click="onOpenDetail">
                查看
              </el-link>
            </div>
            <div class="journal-item">
              <span>v1.0.2 - 2022-08-04</span>
              <el-link :underline="false" type="primary" @click="onOpenDetail">
                查看
              </el-link>
            </div>
          </div>
        </el-scrollbar>
      </template>
    </el-card>

    <el-card class="box-card">
      <template #header>
        <div class="card-header">捐赠支持</div>
      </template>
      <template #default>
        <div class="donation">
          <div class="img">
            <img src="../../../src/assets/images/wx.png" alt="donate" />
            <img src="../../../src/assets/images/al.jpg" alt="donate" />
          </div>
        </div>
      </template>
    </el-card>
  </div>
  <!-- 日志详情弹出框 -->
  <el-dialog v-model="dialogVisible" title="更新详情" width="30%">
    <el-scrollbar class="journalDetail">
      <p>1.初始提交</p>
      <p>2.添加数据库文件</p>
      <p>3.添加前端vue核心程序</p>
      <p>4.修复些BUG 并添加权限指令</p>
      <p>5.修复环境变量配置问题</p>
    </el-scrollbar>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="dialogVisible = false">关闭</el-button>
      </span>
    </template>
  </el-dialog>
</template>

<script>
export default {
  data() {
    return {
      dialogVisible: false
    }
  },
  methods: {
    onOpenDetail() {
      this.dialogVisible = true
    }
  }
}
</script>

<style lang="scss" scoped>
.HomeFooter {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 1rem;

  .box-card {
    height: 310px;
  }

  .contact {
    .contact-item {
      display: flex;
      align-items: center;
      gap: 4px;
      border-bottom: 1px solid var(--el-border-color);
      line-height: 35px;

      .svg {
        width: 16px;
      }

      .title {
        width: 80px;
      }

      .contact-information {
        flex: 1;
      }
    }
  }

  .journal {
    .journal-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid var(--el-border-color);
      line-height: 35px;
    }
  }

  .donation {
    .img {
      display: grid;
      grid-template-columns: 1fr 1fr;
      justify-items: center;
      align-items: center;
      gap: 8px;

      img {
        width: 180px;
        height: 180px;
      }
    }
  }
}
</style>
