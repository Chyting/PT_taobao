<template>
  <div class="login">
    <el-container>
      <el-header height="98px" class="login-header">
        <div class="h-pannel">
          <img src="../../assets/login/mistore_logo.png" alt="" />
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
                    placeholder="邮箱/手机号码/小米ID"
                    autocomplete="off"
                  ></el-input>
                  <el-input
                    placeholder="密码"
                    v-model="password"
                    show-password
                    auto-complete="new-password"
                  ></el-input>
                  <el-button type="primary">登陆</el-button>
                  <p class="text-login">手机短信登陆/注册</p>
                  <div class="regist-or-forget">
                    <a href="">
                      立即注册
                    </a>
                    <span>|</span>
                    <a href="">忘记密码?</a>
                  </div>
                </div>
                <div v-else class="main-form__code-login"></div>
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
import FooterItem from "@/components/layout/footer/index";
export default {
  components: {
    FooterItem
  },
  data() {
    return {
      flag: "accountLogin",
      show: true,
      account: "",
      password: "",
      ACCOUNT_LOGIN,
      CODE_LOGIN
    };
  },
  methods: {
    changeBoard(val) {
      if (val === ACCOUNT_LOGIN) {
        this.flag = ACCOUNT_LOGIN;
      } else {
        this.flag = CODE_LOGIN;
      }
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
}
::v-deep .el-input__inner {
  height: 48px;
  border-radius: 0;
  margin-bottom: 14px;
  padding: 13px 16px 13px 14px;
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
