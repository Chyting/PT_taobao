<template>
  <div class="home">
    <home-page-header></home-page-header>
    <practice></practice>
  </div>
</template>

<script>
import HomePageHeader from "@/components/layout/homePageHeader/index";
import Practice from "./practice/index";
export default {
  name: "Home",
  components: {
    HomePageHeader,
    Practice
  },
  watch: {
    input: {
      handler(newInput, oldInput) {
        console.log(newInput);
        console.log(oldInput);
        this.obj.a = "我是一个测试";
      }
      // immediate: true,
      // deep: true
    },
    obj: {
      handler(newA, oldA) {
        console.log(newA);
        console.log(oldA);
        console.log("我改变了");
      },
      immediate: true,
      deep: true
    }
  },
  data() {
    return {
      input: "罪恶",
      content: "啦啦啦啦",
      obj: {
        a: "341"
      }
    };
  }
};
</script>
<style lang="scss" scoped>
.home {
  width: 100%;
  height: 100%;
}
::v-deep .el-input {
  width: 100px;
}
</style>
