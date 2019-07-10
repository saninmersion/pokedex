<template>
  <PokedexWrapper />
</template>

<script>
import PokedexWrapper from "./components/Pokedex/PokedexWrapper.vue";

export default {
  name: "app",
  components: {
    PokedexWrapper
  }
};
</script>

<style lang="scss">
$pokedex: #fd1a55;
$purple: #481557;

* {
  box-sizing: border-box;
}

body {
  font-family: monospace;
  background: #e7e7e2;
}

#info {
  display: inline-block;
  width: 400px;
  vertical-align: top;
  ul {
    li {
      text-transform: capitalize;
      span {
        font-weight: bold;
      }
    }
  }
}

#search {
  display: block;
  margin: 1em 0;
}

#pokedex {
  background: #ca215b;
  height: 600px;
  width: 400px;
  border-radius: 20px;
  overflow: hidden;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.lights {
  display: inline-block;
  height: 60px;
  width: 400px;
  padding: 10px;
  position: relative;
  z-index: 2;
  background: $pokedex;

  .right-side {
    position: absolute;
    height: 70px;
    width: 250px;
    border-top: 26px solid #481557;
    top: 37px;
    right: -40px;
    border-top-left-radius: 30px;
    z-index: 2;
  }

  &:before {
    content: "";
    background: #fd1a55;
    height: 100px;
    width: 220px;
    border-bottom: 25px solid #481557;
    position: absolute;
    border-radius: 35%;
    top: 20px;
    left: -85px;
  }

  &:after {
    content: "";
    height: 100px;
    width: 185px;
    border-bottom: 27px solid #481557;
    position: absolute;
    border-bottom-left-radius: 30%;
    top: 2px;
    left: 28px;
    transform: rotate(337deg);
    z-index: 0;
  }

  .blue-light {
    height: 60px;
    width: 60px;
    background: #00b5d4;
    border-radius: 50%;
    display: inline-block;
    position: relative;
    overflow: hidden;
    border: 2px solid #00bcd4;
    &:before {
      content: "";
      background: #00dbff;
      height: 55px;
      width: 55px;
      position: absolute;
      border-radius: 55%;
      top: -12px;
      left: -12px;
    }
    &:after {
      content: "";
      height: 11px;
      width: 11px;
      position: absolute;
      background: #ebebeb;
      border-radius: 50%;
      top: 12px;
      left: 10px;
    }
  }
}

.blue-light-holder {
  background: #fff9f1;
  display: inline-block;
  border-radius: 50%;
  height: 74px;
  width: 74px;
  padding-top: 7px;
  padding-left: 7px;
  position: relative;
}

.led-container {
  display: inline-block;
  vertical-align: top;
  position: relative;
  z-index: 0;
  height: 70px;
  background: $pokedex;
  > div {
    height: 20px;
    width: 20px;
    display: inline-block;
    border-radius: 50px;
    margin: 0 1px;
    border: 3px solid #031556;
    position: relative;
    overflow: hidden;
    &:before {
      content: "";
      background: #fff9f1;
      height: 5px;
      width: 5px;
      border-radius: 50%;
      position: absolute;
      top: 2.5px;
      left: 2.1px;
      z-index: 3;
    }
    &:after {
      content: "";
      height: 10px;
      width: 10px;
      position: absolute;
      border-radius: 50%;
      z-index: -1;
      top: 0;
      left: 0;
    }
  }
  .red-light:after,
  .yellow-light:after,
  .green-light:after {
    content: "";
    height: 12px;
    width: 9px;
    z-index: 1;
    top: -1px;
    left: 2px;
    position: absolute;
  }
  .red-light {
    background-color: #cb0022;
    &:after {
      background: red;
    }
  }
  .yellow-light {
    background-color: #ffe01c;
    &:after {
      background: yellow;
    }
  }
  .green-light {
    background-color: #3dba61;
    &:after {
      background: #40d165;
    }
  }
}

.main-module {
  padding: 2em;
  width: 94%;
  height: 550px;
  margin: auto;
  border-bottom-left-radius: 20px;
  border: 5px solid #481557;
  border-top: none;
  margin-top: 123px;
  padding-top: 123px;
  top: -172px;
  position: relative;
  z-index: 1;
}

.outer-screen {
  pointer-events: none;
  background: #f3f4e8;
  height: 250px;
  width: 100%;
  border-radius: 10px;
  padding: 5px 2em 20px 2em;
  margin-bottom: 1.5em;
  box-shadow: 3px 5px 0px 1px $purple;
  position: relative;

  &:before {
    content: "";
    background: #ca215b;
    position: absolute;
    height: 35px;
    width: 70px;
    left: -20px;
    bottom: -15px;
    transform: rotate(40deg);
    z-index: 1;
  }
}

.tiny-lights {
  text-align: center;

  &:before,
  &:after {
    content: "";
    height: 7px;
    width: 7px;
    background: red;
    display: inline-block;
    margin: 3px 5px;
    border-radius: 50%;
    border: 3px solid black;
  }
}

.outerscreen-light {
  height: 32px;
  width: 32px;
  background: #fd1a55;
  display: inline-block;
  border-radius: 50%;
  border: 4px solid black;
  margin-left: 20px;
}

.speaker-container {
  display: inline-block;
  width: 35%;
  float: right;
}

.speaker-container > div {
  height: 7px;
  background: #1a2e5c;
  margin-bottom: 4px;
  border-radius: 20px;
}

.inner-screen {
  height: 80%;
  width: 100%;
  background-color: #b3d7ff;
  border-radius: 5px;
  text-align: center;
  padding: 1em;
  text-transform: capitalize;
  margin-bottom: 5px;
  overflow-x: hidden;
  overflow-y: scroll;
  h3 {
    color: #fff;
    margin: 0;
    font-size: 42px;
  }
  img.pokesprite {
    height: 100%;
    width: auto;
  }
  .pokename {
    font-size: 16px;
    position: absolute;
    left: 50%;
    top: 30px;
    transform: translateX(-60%);
  }
}

.round-btn {
  cursor: pointer;
  height: 43px;
  width: 43px;
  background: #202020;
  border-radius: 50px;
  display: inline-block;
  vertical-align: top;
  position: relative;
  z-index: 1;
  background-image: url("./assets/images/icons/speaker.png");
  background-repeat: no-repeat;
  background-size: auto;
  background-position: center;
}

.btn-screen-container {
  display: inline-block;
  padding: 0 1.5em;
}

.start-select {
  display: flex;
  height: 45px;
  align-items: center;
  justify-content: center;
}

.start-select > div {
  height: 18px;
  width: 60px;
  border-radius: 5px;
  text-align: center;
}

.start,
.select {
  cursor: pointer;
  box-shadow: 2px 3px 0px 0px $purple;
}

.start {
  background-color: #ff002c;
  margin-right: 25px;
}

.select {
  background-color: #03628e;
}

.little-screen {
  background-color: #deebf9;
  padding: 10px;
  height: 100px;
  width: 145px;
  border-radius: 5px;
  overflow: hidden;

  .pokemon_description {
    width: 100%;
    height: 100%;
    overflow-y: scroll;
    padding-right: 24px; /* Increase/decrease this value for cross-browser compatibility */
    box-sizing: content-box; /* So the width will be 100% + 17px */
  }
}

.d-pad {
  display: inline-block;
  vertical-align: top;
  text-align: right;
  width: 87px;
  position: relative;
}

.d-pad > div {
  border-radius: 4px;
  margin-bottom: 35px;
  margin-left: 30px;
}

.dpad-up {
  display: block;
  cursor: pointer;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 0 25px 43.3px 25px;
  border-color: transparent transparent #202020 transparent;
  background: transparent;
}

.dpad-down {
  display: block;
  cursor: pointer;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 43.3px 25px 0 25px;
  border-color: #202020 transparent transparent transparent;
}

.pokemon-list {
  display: inline-block;
  list-style-type: none;
  text-align: center;
  padding: 0;

  li {
    font-size: 22px;
  }

  li:hover {
    background: $pokedex;
    color: white;
  }

  li.selected {
    background: $purple;
    color: white;
  }
}
</style>

