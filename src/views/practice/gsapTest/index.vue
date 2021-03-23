<template>
  <div class="gsap-test">
    <div id="test" x="50" y="100"></div>
    <el-button type="primary" @click="animation">开启动画</el-button>
  </div>
</template>

<script>
import gsap from "gsap";
export default {
  name: "index",
  mounted() {
    console.log(gsap);
  },
  methods: {
    animation() {
      gsap.set("#tes", { transformOrigin: "center" });
      gsap.to("#test", {
        x: 100,
        y: 100,
        fill: "red",
        stroke: "red",
        strokeWidth: 5,
        rotation: 360,
        scaleX: 2,
        duration: 1
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.gsap-test {
  width: 300px;
  height: 300px;
  position: relative;
}
#test {
  width: 50px;
  height: 50px;
  border: 1px solid #ededed;
  background-color: pink;
}
::v-deep .el-button {
  position: absolute;
  bottom: 5px;
}
</style>
