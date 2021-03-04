<template>
  <div class="footer">
    <ul class="footer-item">
      <li><a href="">简体</a></li>
      <li><a href="">繁体</a></li>
      <li><a href="">English</a></li>
      <li><a href="">常见问题</a></li>
      <li><a href="">隐私政策</a></li>
    </ul>
    <p class="footer-desc">
      小米公司版权所有-京ICP备10046444-
      <a
        href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=11010802020134"
      >
        <img src="@/assets/login/ghs.png" alt="ghs" />
        京公网安备11010802020134号
      </a>
      -京ICP证110507号
    </p>
  </div>
</template>

<script>
export default {
  name: "index"
};
</script>

<style lang="scss" scoped>
.footer {
  padding-top: 100px;
  &-item {
    font-size: 14px;
    li {
      display: inline-block;
      a {
        color: #757575;
        &:hover {
          color: black;
          font-weight: 500;
        }
      }
    }
    li::after {
      content: "|";
      margin: 0 10px;
    }
    li:last-child::after {
      content: " ";
    }
  }
  &-desc {
    margin: 10px 0;
    color: #757575;
    font-size: 14px;
    a {
      display: inline-block;
      color: #757575;
      text-decoration: none;
    }
  }
}
</style>
