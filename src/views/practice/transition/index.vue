<template>
  <div class="transition-vue">
    <transition name="fade">
      <div v-if="show">
        <img class="image" src="../../../assets/logo.png" alt="" />
        <p class="src">这是一个logo</p>
      </div>
    </transition>
    <el-button @click="show = !show" size="medium" type="success"
      >过渡</el-button
    >
  </div>
</template>
<script>
export default {
  name: "index.vue",
  data() {
    return {
      show: true
    };
  },
  mounted() {},
  methods: {
    handleClick() {}
  }
};
</script>

<style lang="scss" scoped>
.transition-vue {
  width: 300px;
  height: 200px;
  position: relative;
  border: 1px solid #21aeeb;
}
.image {
  height: 100px;
  width: 100px;
}
.src {
  font-size: 18px;
}
::v-deep .el-button {
  position: absolute;
  left: 118px;
  bottom: 5px;
}
//进入和离开
.fade-enter,
.fade-leave-to {
  color: red;
  transform: translateX(30px);
  opacity: 0;
}
//进入和离开的过程动画
.fade-enter-active {
  transition: all 0.7s ease;
}
.fade-leave-active {
  color: orange;
  transition: all 1s cubic-bezier(1, 0.5, 0.8, 1);
}
</style>
