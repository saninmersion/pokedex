<template>
  <div class="lights">
    <div class="blue-light-holder">
      <div class="blue-light"></div>
    </div>
    <div class="right-side"></div>
    <div class="led-container">
      <div class="red-light"></div>
      <div class="yellow-light"></div>
      <div class="green-light"></div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Lights"
};
</script>

<style lang="scss">
.led-container > .red-light,
.led-container > .red-light::after {
  animation: red-color-transition 2s linear infinite 3s reverse;
}
.led-container > .yellow-light,
.led-container > .yellow-light::after {
  animation: yellow-color-transition 2s linear infinite 3s reverse;
}
.led-container > .green-light,
.led-container > .green-light::after {
  animation: green-color-transition 2s linear infinite 3s reverse;
}

@keyframes red-color-transition {
  0% {
    background: red;
  }
  20% {
    background: yellow;
  }
  100% {
    background: green;
  }
}
@keyframes yellow-color-transition {
  0% {
    background: yellow;
  }
  50% {
    background: green;
  }
  100% {
    background: red;
  }
}
@keyframes green-color-transition {
  0% {
    background: green;
  }
  50% {
    background: red;
  }
  100% {
    background: yellow;
  }
}
</style>

