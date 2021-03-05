<template>
  <div class="login">
    <el-container>
      <el-header height="98px" class="login-header">
        <div class="h-pannel">
          <a href="https://www.mi.com/index.html">
            <img src="../../assets/login/mistore_logo.png" alt="" />
          </a>
        </div>
      </el-header>
      <el-main>
        <div class="main-bgc">
          <a
            href="https://www.mi.com/redmi10x-5G"
            class="bgc-a"
            target="_parent"
          ></a>
          <div class="main-formbgc">
            <div class="main-form">
              <div class="main-form__title">
                <a
                  :class="{ now: flag === ACCOUNT_LOGIN }"
                  class="native-link"
                  href="javascript:void(0);"
                  @click="changeBoard(ACCOUNT_LOGIN)"
                  >账户登陆</a
                >
                <span class="line"></span>
                <a
                  :class="{ now: flag === CODE_LOGIN }"
                  href="javascript:void(0);"
                  class="native-link"
                  @click="changeBoard(CODE_LOGIN)"
                  >扫码登陆</a
                >
              </div>
              <div class="main-form__content">
                <div v-if="show" class="main-form__account-login">
                  <el-input
                    v-model="account"
                    :placeholder="
                      loginMethod ? '邮箱/手机号码/小米ID' : '手机号码'
                    "
                    autocomplete="off"
                  >
                    <template slot="prepend" v-if="!loginMethod">+86</template>
                  </el-input>
                  <el-input
                    :placeholder="loginMethod ? '密码' : '短信验证码'"
                    v-model="password"
                    show-password
                    auto-complete="new-password"
                  >
                    <template slot="append" v-if="!loginMethod"
                      >获取验证码
                      <div class="shadeBox" @click="getCode"></div
                    ></template>
                  </el-input>
                  <el-button type="primary" @click="login">{{
                    loginMethod ? "登陆" : "立即登录/注册"
                  }}</el-button>
                  <p class="text-login" @click="changeLoginMethod">
                    {{ loginMethod ? "手机短信登陆/注册" : "用户名密码登陆" }}
                  </p>
                  <div class="regist-or-forget">
                    <div v-if="loginMethod">
                      <a href="">
                        立即注册
                      </a>
                      <span>|</span>
                      <a href="">忘记密码?</a>
                    </div>
                    <div v-else>
                      <a
                        href="https://account.xiaomi.com/helpcenter/faq/zh_CN/02.faqs/05.sms-and-email-verification-code/faq-1"
                        >收不到验证码？</a
                      >
                    </div>
                  </div>
                  <div class="main-form__link">
                    <a href="" class="link-qq link-icon">
                      <i class="btn_sns_icontype"></i>
                    </a>
                    <a href="" class="link-weibo link-icon">
                      <i class="btn_sns_icontype"></i>
                    </a>
                    <a href="" class="link-zhifubao link-icon">
                      <i class="btn_sns_icontype"></i>
                    </a>
                    <a href="" class="link-weixin link-icon">
                      <i class="btn_sns_icontype"></i>
                    </a>
                  </div>
                </div>
                <div v-else class="main-form__code-login">
                  <p class="qrcode-text">
                    请使用小米手机/米家等小米旗下APP扫码登录
                  </p>
                  <i class="qrcode-help"></i>
                  <vue-qr
                    :logoSrc="imageUrl"
                    text="上当了吧大傻逼0*0"
                    :size="240"
                  ></vue-qr>
                  <p>使用<span class="xmApp">小米商城APP</span>扫一扫</p>
                  <p>小米手机可打开「设置」>「小米帐号」扫码登录</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </el-main>
      <el-footer>
        <footer-item></footer-item>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
const ACCOUNT_LOGIN = "accountLogin";
const CODE_LOGIN = "codeLogin";
const USERNAME_LOGIN = "usernameLogin";
const PHONE_LOGIN = "phoneLogin";
import FooterItem from "@/components/layout/footer/index";
import vueQr from "vue-qr";
export default {
  components: {
    FooterItem,
    vueQr
  },
  data() {
    return {
      flag: "accountLogin",
      show: true,
      account: "",
      password: "",
      loginMethod: true,
      ACCOUNT_LOGIN,
      CODE_LOGIN,
      USERNAME_LOGIN,
      PHONE_LOGIN,
      imageUrl: require("../../assets/logo.jpeg")
    };
  },
  mounted() {},
  filters: {},
  methods: {
    login() {
      this.$router.push({
        name: "Home"
      });
    },
    changeBoard(val) {
      if (val === ACCOUNT_LOGIN) {
        this.flag = ACCOUNT_LOGIN;
        this.show = true;
      } else {
        this.flag = CODE_LOGIN;
        this.show = false;
      }
    },
    changeLoginMethod() {
      this.loginMethod = !this.loginMethod;
    },
    getCode() {
      this.$message({
        message: "这只是一个网站测试哟~亲",
        type: "success"
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.login {
  height: 100%;
  width: 100%;
}
.login-header {
  .h-pannel {
    width: 1130px;
    height: 100%;
    margin: 0 auto;
    text-align: left;
    img {
      height: 100%;
    }
  }
}
.main {
  &-bgc {
    width: 100%;
    height: 588px;
    background: url(../../assets/login/bgc.jpg) no-repeat;
    background-position: top center;
    .bgc-a {
      display: block;
      height: 588px;
      text-indent: -9999em;
    }
  }
  &-formbgc {
    width: 1130px;
    position: relative;
    margin: 0 auto;
  }
  &-form {
    position: absolute;
    width: 410px;
    height: 556px;
    background-color: white;
    right: 0;
    bottom: 0;
    &__title {
      padding: 27px 0 24px;
      margin: 0 auto;
      font-size: 24px;
      color: black;
      a {
        text-decoration: none;
        color: #666;
      }
      .now {
        color: #f56600;
      }
      .line {
        width: 1px;
        height: 24px;
        margin: 0 35px 0 42px;
        border: 1px solid #e0e0e0;
        background: #e0e0e0;
      }
    }
    &__account-login {
      .text-login {
        cursor: pointer;
        color: #ff6700;
      }
      .regist-or-forget {
        margin-top: 25px;
        p {
          color: #999;
        }
        a {
          text-decoration: none;
          color: #999;
          &:hover {
            color: #ff6700;
          }
        }
        span {
          margin: 0 8px;
          color: #999;
        }
      }
      .shadeBox {
        background-color: transparent;
        position: absolute;
        top: 0;
        left: 0;
        width: 90px;
        height: 48px;
        z-index: 1000;
      }
    }
    &__code-login {
      p {
        color: #757575;
        margin-top: 3px;
      }
      .qrcode-text {
        margin-top: 70px;
        display: inline-block;
        color: #757575;
      }
      .qrcode-help {
        width: 18px;
        height: 18px;
        background: url("../../assets/login/icon_help.png");
        display: inline-block;
        vertical-align: middle;
      }
      .xmApp {
        margin: 0 4px;
        color: #ff6700;
      }
    }
    &__link {
      margin-top: 150px;
      .link {
        &-qq {
          background-color: #0288d1;
          i {
            background-position: -18px 0;
          }
        }
        &-weibo {
          background-color: #d32f2f;
          i {
            background-position: -37px 0;
          }
        }
        &-zhifubao {
          background-color: #00aaee;
          i {
            background-position: -58px 0;
            width: 24px;
          }
        }
        &-weixin {
          background-color: #00d20d;
          margin-right: 0 !important;
          i {
            background-position: -84px 0;
            width: 24px;
          }
        }
      }
      .btn_sns_icontype {
        display: block;
        margin: 6px auto 0;
        width: 20px;
        height: 20px;
        vertical-align: middle;
        background: url("../../assets/login/icons_type.png") no-repeat;
      }
      .link-icon {
        width: 31px;
        height: 31px;
        border-radius: 50%;
        display: inline-block;
        margin-right: 35px;
      }
    }
    .native-link {
      &:hover {
        color: #f56600;
      }
    }
  }
}
//更改外层容器样式
::v-deep .el-container {
  .el-main {
    padding: 0;
  }
}

//更改input框样式
::v-deep .el-input {
  width: 346px;
  margin-bottom: 14px;
}
::v-deep .el-input__inner {
  height: 48px;
  border-radius: 0;
  padding: 13px 16px 13px 14px;
}
::v-deep .el-input-group__prepend {
  background-color: white;
  color: black;
}
::v-deep .el-input-group__append {
  position: relative;
  padding: 0 10px;
  background-color: white;
  color: #003ab5;
  cursor: pointer;
}
::v-deep .el-button {
  width: 346px;
  border-radius: 0;
  padding: 17px 20px;
  margin: 10px 0;
  &--primary {
    background-color: #ff6700;
    border-color: #ff6700;
  }
}
</style>
