<template>
  <div class="home">
    <home-page-header></home-page-header>
  </div>
</template>

<script>
import HomePageHeader from "@/components/layout/homePageHeader/index";
export default {
  name: "Home",
  components: {
    HomePageHeader
  }
};
</script>
<style lang="scss" scoped>
.home {
  width: 100%;
  height: 100%;
}
</style>
