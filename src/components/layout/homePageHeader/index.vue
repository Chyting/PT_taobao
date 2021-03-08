<template>
  <div class="header">
    <div class="header-navs">
      <div class="header-navs__item">
        <div class="navs-item__left">
          <ul class="lists-left">
            <li>小米商城</li>
            <li>MIUI</li>
            <li>loT</li>
            <li>云服务</li>
            <li>天星数科</li>
            <li>有品</li>
            <li>小爱开放平台</li>
            <li>企业团购</li>
            <li>资质证照</li>
            <li>协议规则</li>
            <li>下载app</li>
            <li>智能生活</li>
            <li class="list-13">Select Location</li>
          </ul>
        </div>
        <div class="navs-item__right">
          <ul class="lists-right">
            <li>
              <a href="javascript:void(0)" @click="jump('login')">登陆</a>
            </li>
            <li><a href="javascript:void(0)">注册</a></li>
            <li class="list-3"><a href="javascript:void(0)">消息通知</a></li>
          </ul>
          <div class="shopping-cart">
            <a href="" slot="reference">
              <i class="el-icon-shopping-cart-2"></i>购物车（<span>{{
                cartCount
              }}</span
              >）</a
            >
          </div>
        </div>
      </div>
    </div>
    <div class="header-list"></div>
  </div>
</template>

<script>
export default {
  name: "index",
  data() {
    return {
      cartCount: 0
    };
  },
  methods: {
    jump(name) {
      this.$router.push({
        name: name
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.header {
  width: 100%;
  height: 140px;
}
.header-navs {
  width: 100%;
  font-size: 12px;
  color: #b0b0b0;
  background-color: #333;
  &__item {
    width: 1226px;
    height: 40px;
    line-height: 40px;
    margin: 0 auto;
  }
}
.navs-item {
  ul li a:hover {
    color: white;
  }
  &__left {
    float: left;
    .lists-left {
      li {
        display: inline-block;
      }
      li::after {
        content: "|";
        margin: 0 6px;
        color: #424242;
      }
      .list-13::after {
        content: "";
      }
    }
  }
  &__right {
    float: right;
    .lists-right {
      display: inline-block;
      li {
        display: inline-block;
        cursor: pointer;
        a {
          text-decoration: none;
          color: #b0b0b0;
        }
      }
      li::after {
        content: "|";
        margin: 0 6px;
        color: #424242;
      }
    }
    .shopping-cart {
      width: 100px;
      height: 100%;
      background-color: #424242;
      margin-left: 10px;
      display: inline-block;
      cursor: pointer;
      a {
        color: #b0b0b0;
        text-decoration: none;
      }
      .el-icon-shopping-cart-2 {
        margin-right: 4px;
        margin-left: 6px;
        font-size: 20px;
        vertical-align: middle;
      }
    }
    .shopping-cart:hover {
      background-color: white;
      a {
        color: #f56600;
      }
    }
  }
}
</style>
