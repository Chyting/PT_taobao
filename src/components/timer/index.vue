<template>
  <div class="flip down go">
    <div class="digital front number0"></div>
    <div class="digital back number1"></div>
  </div>
</template>

<script>
export default {
  name: "index"
};
</script>

<style lang="scss" scoped>
//设置计时框
.flip {
  display: inline-block;
  position: relative;
  width: 60px;
  height: 100px;
  color: #fff;
  line-height: 100px;
  font-size: 66px;
  border: 1px solid #000000;
  border-radius: 10px;
  background: #fff;
  box-shadow: 0 0 6px rgba(0, 0, 0, 0.5);
  text-align: center;
  font-family: "Helvetica Neue";
}

//设置翻牌上下两部分
.flip .digital:before,
.flip .digital:after {
  content: " ";
  position: absolute;
  left: 0;
  right: 0;
  background-color: #000000;
  overflow: hidden;
  box-sizing: border-box;
}
.flip .digital:before {
  top: 0;
  bottom: 50%;
  border-radius: 10px 10px 0 0;
  border-bottom: 1px solid #666;
}
.flip .digital:after {
  bottom: 0;
  top: 50%;
  border-radius: 0 0 10px 10px;
}
//设置下半部分的翻牌数字位置
.flip .digital:after {
  line-height: 0;
}
/**
向下翻牌
*/
.flip.down .front:before {
  z-index: 3;
}
.flip.down .front:after,
.flip.down .back:before {
  z-index: 1;
}
.flip.down .back:after {
  z-index: 2;
  transform-origin: 50% 0%;
  transform: perspective(160px) rotateX(180deg);
}

/**
 向上翻牌
 */
.flip.up .front:after {
  z-index: 3;
}
.flip.up .back:before {
  z-index: 2;
  transform-origin: 50% 100%;
  transform: perspective(160px) rotateX(-180deg);
}
.flip.up .front:before,
.flip.up .back:after {
  z-index: 1;
}
//动画翻转
.flip.down.go .front:before {
  transform-origin: 50% 100%;
  animation: frontFlipDown 0.6s ease-in-out both;
  box-shadow: 0 -2px 6px rgba(255, 255, 255, 0.3);
}
.flip.down.go .back:after {
  animation: backFlipDown 0.6s ease-in-out both;
}
@keyframes frontFlipDown {
  0% {
    transform: perspective(160px) rotateX(0deg);
  }
  100% {
    transform: perspective(160px) rotateX(-180deg);
  }
}
@keyframes backFlipDown {
  0% {
    transform: perspective(160px) rotateX(180deg);
  }
  100% {
    transform: perspective(160px) rotateX(0deg);
  }
}
//设置翻牌数字
.flip .number0:before,
.flip .number0:after {
  content: "0";
}
.flip .number1:before,
.flip .number1:after {
  content: "1";
}
.flip .number2:before,
.flip .number2:after {
  content: "2";
}
.flip .number3:before,
.flip .number3:after {
  content: "3";
}
.flip .number4:before,
.flip .number4:after {
  content: "4";
}
.flip .number5:before,
.flip .number5:after {
  content: "5";
}
.flip .number6:before,
.flip .number6:after {
  content: "6";
}
.flip .number7:before,
.flip .number7:after {
  content: "7";
}
.flip .number8:before,
.flip .number8:after {
  content: "8";
}
.flip .number9:before,
.flip .number9:after {
  content: "9";
}
</style>
