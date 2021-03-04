<template>
  <div class="hello">
    <a href="javascript:viod(0)" class="xm-login" @click="jump('login')"
      >登陆</a
    >
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {},
  methods: {
    jump(name) {
      this.$router.push({
        name: name
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.xm-login {
  text-decoration: none;
}
</style>
