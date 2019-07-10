<template>
  <div id="pokedex">
    <lights />

    <div class="main-module">
      <screen
        :pokemons="pokemons"
        :current="currentPokemon"
        :selected="selectedIndex"
        :mode="this.mode"
      ></screen>

      <controls
        :pokemon="currentPokemon"
        @up-clicked="selectPokemonUp"
        @down-clicked="selectPokemonDown"
        @start-clicked="handleStart"
        @select-clicked="handleSelect"
      ></controls>
    </div>
  </div>
</template>

<script>
import LightsVue from "./partials/Lights.vue";
import ScreenVue from "./partials/Screen.vue";
import ControlsVue from "./partials/Controls.vue";

export default {
  name: "PokedexWrapper",

  components: {
    lights: LightsVue,
    screen: ScreenVue,
    controls: ControlsVue
  },

  data() {
    return {
      pokemons: {},
      currentPokemon: {},
      selectedIndex: 0,
      mode: "list", // can be either list or detail
      counter: 0
    };
  },

  mounted() {
    this.pokemons = require("./../../data/data.json");
  },

  methods: {
    handleSelect() {
      this.currentPokemon = this.pokemons[this.selectedIndex];
      this.mode = "detail";
      this.describe(this.currentPokemon);
      this.typeWriter(this.currentPokemon);
    },

    handleStart() {
      this.currentPokemon = {};
      this.mode = "list";

      var el = document.getElementsByClassName("inner-screen")[0];
      if (this.selectedIndex > 2) {
        el.scrollTop = this.findScrollHeight();
      }

      var el = document.getElementsByClassName("typewrite")[0];
      el.innerHTML = "";
    },

    setMode(type) {
      this.mode = type;
    },

    selectPokemonUp() {
      this.selectedIndex =
        this.selectedIndex === 0 ? this.selectedIndex : this.selectedIndex - 1;
      var el = document.getElementsByClassName("inner-screen")[0];
      var li = document.querySelector("li.selected");

      if (this.selectedIndex < this.pokemons.length) {
        el.scrollTop = el.scrollTop - li.clientHeight;
      }
    },

    selectPokemonDown() {
      this.selectedIndex =
        this.selectedIndex === this.pokemons.length - 1
          ? this.selectedIndex
          : this.selectedIndex + 1;
      var el = document.getElementsByClassName("inner-screen")[0];
      var li = document.querySelector("li.selected");

      if (this.selectedIndex > 2) {
        el.scrollTop = el.scrollTop + li.clientHeight;
      }
    },

    describe: function(pokemon) {
      const synth = window.speechSynthesis;
      synth.cancel();
      const speech = new SpeechSynthesisUtterance();
      speech.text = `${pokemon.name}. ${pokemon.species}. ${pokemon.description}`;
      speech.rate = 1;
      speech.pitch = 1;
      synth.speak(speech);
    },

    typeWriter() {
      var text =
        this.currentPokemon.name +
        "\n" +
        this.currentPokemon.species +
        "\n" +
        this.currentPokemon.description;
      var el = document.getElementsByClassName("typewrite")[0];
      el.scrollTop = el.scrollHeight;
      if (this.counter < text.length) {
        el.innerHTML += text.charAt(this.counter);
        this.counter++;
        setTimeout(this.typeWriter, 65);
      }
    },
    findScrollHeight() {
      var height = 0;
      var el = document.querySelectorAll(".pokemon-list li");
              console.log(el);

      for (var i = 0; i < el.length; i++) {
        if (el[i].className.match(/\bselected\b/)) {
          break;
        }
        if (i < 2) {
          continue;
        }
        height += el[i].clientHeight;
      }
      return height;
    }
  }
};
</script>
