<template>
  <div class="controls">
    <div class="round-btn" @click="()=>{typeWriter(); describe()}"></div>
    <div class="btn-screen-container">
      <div class="little-screen">
        <p class="typewrite pokemon_description"></p>
      </div>
      <div class="start-select">
        <div class="start" @click="$emit('start-clicked', true)">Start</div>
        <div class="select" @click="$emit('select-clicked', true)">Select</div>
      </div>
    </div>
    <div class="d-pad">
      <div class="dpad-up" @click="$emit('up-clicked', true)"></div>
      <div class="dpad-down" @click="$emit('down-clicked', true)"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Controls",
  props: {
    pokemon: {}
  },
};
</script>

