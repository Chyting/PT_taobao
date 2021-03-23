<template>
  <div class="practice">
    <transition></transition>
    <gsap-test></gsap-test>
  </div>
</template>

<script>
import Transition from "./transition/index";
import GsapTest from "./gsapTest/index";
export default {
  name: "index.vue",
  components: {
    Transition,
    GsapTest
  }
};
</script>

<style lang="scss" scoped>
.practice {
  height: 500px;
  display: flex;
  justify-content: space-between;
  margin: 20px 10px 0;
  border: 1px solid #fff;
  box-shadow: 0 0 5px #f19f74;
}
</style>
