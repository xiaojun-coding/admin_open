<template>
  <div class="Login">
    <el-form class="login-form" ref="formRef" :model="form" :rules="rules">
      <el-form-item>
        <h2 class="login-title">小鹿线基础框架</h2>
      </el-form-item>

      <el-form-item prop="username">
        <el-input
          size="large"
          v-model="form.username"
          placeholder="用户名"
          @keyup.enter="onSubmit"
        >
          <template #prefix>
            <IconUser />
          </template>
        </el-input>
      </el-form-item>

      <el-form-item prop="password">
        <el-input
          size="large"
          v-model="form.password"
          placeholder="密码"
          show-password
          @keyup.enter="onSubmit"
        >
          <template #prefix>
            <IconPwd></IconPwd>
          </template>
        </el-input>
      </el-form-item>

      <el-form-item prop="captcha">
        <div class="form-code">
          <el-input
            class="code-input"
            size="large"
            v-model="form.captcha"
            :maxlength="4"
            show-word-limit
            placeholder="验证码"
            @keyup.enter="onSubmit"
          >
            <template #prefix>
              <IconCode></IconCode>
            </template>
          </el-input>
          <el-image
            :src="verificationCode.src"
            class="code-img"
            @click="loadVerificationCodeImg"
          >
            <template #error>
              <el-icon><Picture /></el-icon>
            </template>
          </el-image>
        </div>
      </el-form-item>

      <el-form-item>
        <el-checkbox v-model="memoPassword" @change="onMemoPasswordChange">
          记住密码
        </el-checkbox>
      </el-form-item>

      <el-form-item>
        <el-button
          size="large"
          type="primary"
          class="form-submit"
          @click="onSubmit"
        >
          登录
        </el-button>
      </el-form-item>
    </el-form>
  </div>

  <Copyright />
</template>

<script>
import { enCryptoAES } from "@share/helper/crypto"
import { ApiCaptchaImageCode, ApiLogin } from "@api/index.js"
import { useGlobalUserStore } from "@store/UserGlobalStore"
import Copyright from "../common/Copyright.vue"

export default {
  name: "Login",
  data() {
    return {
      rules: {
        username: [
          { required: true, message: "用户名是必填项", trigger: "blur" }
        ],
        password: [
          { required: true, message: "用户密码是必填项", trigger: "blur" }
        ],
        captcha: [{ required: true, message: "请输入验证码", trigger: "blur" }]
      },
      form: {
        username: "",
        password: "",
        captcha: ""
      },
      verificationCode: {
        src: "default",
        curKey: ""
      },
      memoPassword:
        localStorage.getItem("memoPassword") === "true" ? true : false
    }
  },
  methods: {
    init() {
      this.loadVerificationCodeImg()
    },
    async loadVerificationCodeImg() {
      const key = new Date().getTime()
      const src = await ApiCaptchaImageCode({ key })
      console.log(src)
      this.verificationCode.src = src
      this.verificationCode.curKey = key
    },
    async onSubmit() {
      try {
        // 登录
        await this.$refs.formRef.validate()
        const store = useGlobalUserStore()
        const { username, password, captcha } = this.form
        const params = {
          username: enCryptoAES(username),
          password: enCryptoAES(password),
          key: this.verificationCode.curKey,
          captcha
        }
        const token = await ApiLogin(params)
        localStorage.setItem("token", token)

        await store.initUserInfoAndConfig()

        this.setMemoPassword()
        this.$router.push("/")
      } catch (e) {
        if (typeof e === "object" && ["10013", "10022"].includes(e.code)) {
          this.loadVerificationCodeImg()
        }
        return
      }
    },
    /* --------------  -------------- */
    setMemoPassword() {
      this.memoPassword
        ? localStorage.setItem(
            "user-pwd",
            JSON.stringify({
              name: this.form.username,
              pwd: this.form.password
            })
          )
        : localStorage.removeItem("user-pwd")
    },
    onMemoPasswordChange(value) {
      localStorage.setItem("memoPassword", (this.memoPassword = value))
    },
    recoverPwd() {
      if (!this.memoPassword) {
        return
      }

      const userInfo = localStorage.getItem("user-pwd")
      if (!userInfo) {
        return
      }

      const { name, pwd } = JSON.parse(userInfo)
      this.form.username = name
      this.form.password = pwd
    }
  },
  components: { Copyright },
  mounted() {
    this.recoverPwd()
    this.init()
  }
}
</script>

<style lang="scss" scoped>
.Login {
  position: fixed;
  inset: 0;
  background: url("@assets/images/login_bg.webp") no-repeat center top;
  background-size: cover;
  overflow: hidden;

  display: flex;
  justify-content: center;
  align-items: center;
}

.login-form {
  padding: 3rem 2rem;
  width: 400px;
  background: #fff;

  .el-form-item:last-child {
    margin-bottom: 0;
  }

  .login-title {
    width: 100%;
    text-align: center;
    font-weight: bold;
    font-size: 1.25rem;
  }

  .form-code {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
    width: 100%;

    .code-input {
      flex: 1;
    }

    .code-img {
      width: 100px;
      height: 40px;
      cursor: pointer;
    }
  }

  .form-submit {
    width: 100%;
  }
}

.Copyright {
  position: fixed;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 2;
}
</style>
