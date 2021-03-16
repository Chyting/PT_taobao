<template>
  <div class="drop-down-menu" style="width:550px">
    <div ref="titleHeight" class="menu-title">
      <div class="list" v-for="item in products" :key="item.name">
        {{ item.name }}
      </div>
    </div>
    <div
      :style="{ width: dropWidth + 'px', top: offsetHeight + 'px' }"
      class="menu-goods"
    >
      <div class="goods-list">
        <ul class="xm-lists">
          <li
            class="product"
            v-for="item in chooseProductsList"
            :key="item.index"
          >
            <a href="">
              <img class="product_img" :src="item.src" alt="小米10s" />
              <p class="product_name">{{ item.name }}</p>
              <p class="product_price">{{ item.price }}元起</p>
            </a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
// import $ from "jquery";
export default {
  name: "index",
  props: {
    products: {
      type: Array,
      default() {
        return [];
      }
    }
  },
  data() {
    return {
      chooseProductsList: [],
      offsetHeight: 100,
      dropWidth: 1919
    };
  },
  mounted() {
    this.getTopHeight();
    this.chooseType();
  },
  methods: {
    getTopHeight() {
      const a = this.$refs.titleHeight;
      this.offsetHeight = a.offsetHeight;
    },
    chooseType() {
      let div = document.getElementsByClassName("list");
      const _this = this;
      for (let i = 0; i < div.length; i++) {
        div[i].onmouseover = function() {
          console.log(div[i].innerHTML);
          _this.chooseProductsList = _this.products[i].items;
        };
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.drop-down-menu {
  height: 100%;
  position: relative;
  cursor: pointer;
  margin: 0 auto;
}
.drop-down-menu:hover .menu-goods {
  height: 200px;
  transition: all 0.3s;
  opacity: 1;
  //background-color: #ded6ee;
  .xm-lists {
    visibility: visible;
    opacity: 1;
  }
}

.menu {
  &-title {
    height: 100%;
    display: flex;
    justify-content: space-around;
    font-size: 18px;
    .list {
      line-height: 100px;
    }
    .list:hover {
      color: #fc642c;
      transition: all 0.2s;
    }
  }
  &-goods {
    position: absolute;
    left: -684px;
    height: 0;
    margin: 0 auto;
    opacity: 0;
    box-shadow: 0 3px 4px #ededed;
    border-top: 1px solid #e0e0e0;
    transition: all 0.3s;
    .goods-list {
      margin: 0 18%;
      height: 100%;
      .xm-lists {
        visibility: hidden;
        opacity: 0;
        margin-top: 24px;
        li {
          display: inline-block;
        }
        li:before {
          position: absolute;
          left: 0;
          top: 35px;
          z-index: 1;
          width: 1px;
          height: 100px;
          content: "";
          background-color: #e0e0e0;
        }
      }
      .product {
        a {
          text-decoration: none;
        }
        .product_img {
          width: 160px;
          height: 110px;
          border-right: 1px solid #ededed;
        }
        &_price {
          color: #f56600;
        }
      }
    }
  }
}
</style>
