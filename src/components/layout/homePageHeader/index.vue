<template>
  <div class="header">
    <div class="header-navs">
      <div class="header-navs__item">
        <div class="navs-item__left">
          <ul class="lists-left">
            <li><a href="">小米商城</a></li>
            <li><a href="https://home.miui.com/">MIUI</a></li>
            <li><a href="https://iot.mi.com/">loT</a></li>
            <li><a href="https://i.mi.com/">云服务</a></li>
            <li><a href="https://airstar.com/home">天星数科</a></li>
            <li><a href="https://www.xiaomiyoupin.com/">有品</a></li>
            <li><a href="https://xiaoai.mi.com/">小爱开放平台</a></li>
            <li><a href="https://qiye.mi.com/">企业团购</a></li>
            <li>
              <a href="https://www.mi.com/aptitude/list?id=41">资质证照</a>
            </li>
            <li><a href="">协议规则</a></li>
            <li><a href="">下载app</a></li>
            <li><a href="">智能生活</a></li>
            <li class="list-13"><a href="">Select Location</a></li>
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
            <div class="shopping-cart__drop-down-box">
              <div class="goods-list" v-if="hasGoods"></div>
              <div class="null-good-list" v-else>
                购物车中暂时没有东西哦~
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="header-list">
      <div class="lists">
        <div class="lists-logo">
          <a href="" title="小米官网"></a>
        </div>
        <div class="lists-nav">
          <drop-down :products="testList"></drop-down>
        </div>
        <div class="lists-search"></div>
      </div>
    </div>
  </div>
</template>
<script>
import DropDown from "@/components/dropDown/index";
export default {
  name: "index",
  components: {
    DropDown
  },
  data() {
    return {
      testList: [
        {
          type: "xiaomi",
          name: "小米手机",
          items: [
            {
              name: "小米10S",
              price: 3299,
              link: "mi10S",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/f9149ef3ba2c9025a4a21c98ae793808.png?thumb=1&w=160&h=110&f=webp&q=90"
            },
            {
              name: "小米11",
              price: 3299,
              link: "mi11",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/963679eaf3937351e154600ab3448460.png?thumb=1&w=160&h=110&f=webp&q=90"
            }
          ]
        },
        {
          type: "redmi",
          name: "Redmi红米",
          items: [
            {
              name: "K40 Pro 系列",
              price: 2799,
              link: "k40pro-series",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png?thumb=1&w=160&h=110&f=webp&q=90"
            },
            {
              name: "Redmi K40",
              price: 5100,
              link: "redmi40",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/7bd1b02e0329bd5c41d193f01349f991.jpg?thumb=1&w=160&h=110&f=webp&q=90"
            }
          ]
        },
        {
          type: "tv",
          name: "电视",
          items: [
            {
              name: "K40 Pro 系列",
              price: 2799,
              link: "k40pro-series",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png?thumb=1&w=160&h=110&f=webp&q=90"
            },
            {
              name: "Redmi K40",
              price: 5100,
              link: "redmi40",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/7bd1b02e0329bd5c41d193f01349f991.jpg?thumb=1&w=160&h=110&f=webp&q=90"
            }
          ]
        },
        {
          type: "notebook",
          name: "笔记本",
          items: [
            {
              name: "K40 Pro 系列",
              price: 2799,
              link: "k40pro-series",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png?thumb=1&w=160&h=110&f=webp&q=90"
            },
            {
              name: "Redmi K40",
              price: 5100,
              link: "redmi40",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/7bd1b02e0329bd5c41d193f01349f991.jpg?thumb=1&w=160&h=110&f=webp&q=90"
            }
          ]
        },
        {
          type: "applances",
          name: "家电",
          items: [
            {
              name: "K40 Pro 系列",
              price: 2799,
              link: "k40pro-series",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png?thumb=1&w=160&h=110&f=webp&q=90"
            },
            {
              name: "Redmi K40",
              price: 5100,
              link: "redmi40",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/7bd1b02e0329bd5c41d193f01349f991.jpg?thumb=1&w=160&h=110&f=webp&q=90"
            }
          ]
        },
        {
          type: "router",
          name: "路由器",
          items: [
            {
              name: "K40 Pro 系列",
              price: 2799,
              link: "k40pro-series",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/d07671f25a2b3a6c3d4fac189f28fbe9.png?thumb=1&w=160&h=110&f=webp&q=90"
            },
            {
              name: "Redmi K40",
              price: 5100,
              link: "redmi40",
              src:
                "//cdn.cnbj1.fds.api.mi-img.com/mi-mall/7bd1b02e0329bd5c41d193f01349f991.jpg?thumb=1&w=160&h=110&f=webp&q=90"
            }
          ]
        }
      ],
      cartCount: 0,
      hasGoods: false
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
.header-list {
  width: 100%;
  .lists {
    width: 1226px;
    height: 100px;
    margin: 0 auto;
    position: relative;
    &-logo {
      float: left;
      margin-top: 22px;
      a {
        position: relative;
        height: 55px;
        width: 55px;
        display: block;
        overflow: hidden;
        background-color: #f56600;
        &:hover:before {
          transform: translate3d(55px, 0, 0);
          opacity: 0;
        }
        &:hover:after {
          opacity: 1;
          margin-left: 0;
        }
        &::before {
          position: absolute;
          left: 0;
          top: 0;
          z-index: 1;
          width: 55px;
          height: 55px;
          content: "";
          background: url("../../../assets/homePage/mi-logo.png") no-repeat 50%
            50%;
          transition: all 0.2s;
          opacity: 1;
        }
        &::after {
          position: absolute;
          left: 0;
          top: 0;
          z-index: 1;
          width: 55px;
          height: 55px;
          content: "";
          margin-left: -55px;
          background: url("../../../assets/homePage/mi-home.png") no-repeat 50%
            50%;
          transition: all 0.2s;
          opacity: 0;
        }
      }
    }
    &-nav {
      height: 100%;
      .nav-list {
        .nav-item:hover a {
          color: #f56600;
        }
        .item-children {
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          height: 80px;
          border: 1px solid #ededed;
        }
      }
    }
    &-search {
    }
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
        a {
          color: #b0b0b0;
          text-decoration: none;
        }
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
      position: relative;
      background-color: #424242;
      margin-left: 10px;
      display: inline-block;
      a {
        color: #b0b0b0;
        height: 40px;
        display: block;
        text-decoration: none;
      }
      a:hover {
        background-color: white;
        color: #f56600;
      }
      &:hover {
        .shopping-cart__drop-down-box {
          display: block;
          height: 100px;
        }
      }
      .el-icon-shopping-cart-2 {
        margin-right: 4px;
        margin-left: 6px;
        font-size: 20px;
        vertical-align: middle;
      }
      &__drop-down-box {
        position: absolute;
        width: 316px;
        left: -214px;
        top: 39px;
        display: none;
        border: 1px solid black;
        .null-good-list {
          padding: 20px 0 20px;
          color: black;
          display: none;
        }
      }
    }
  }
}
</style>
