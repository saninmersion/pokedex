<template>
  <div class="outer-screen">
    <div class="tiny-lights"></div>
    <div class="inner-screen">
      <p v-if="isDetailMode" class="pokename"><strong>{{current.name}}</strong></p>
      <img v-if="isDetailMode" class="pokesprite" :src="current.sprite" :alt="current.name" />
      <ul v-show="!isDetailMode" class="pokemon-list">
        <li v-for="(pokemon, index) in pokemons" 
            :key="index" 
            :class="{'selected':selected===index}"
            @click="()=>{$emit('change-pokemon',pokemon.name); isDetailMode = true;}">
          {{ pokemon.name }}
        </li>
      </ul>
    </div>
    <div class="outerscreen-light" @click="describe(current)">
    </div>
    <div class="speaker-container">
      <div></div>
      <div></div>
      <div></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Screen",
  props:{
    "pokemons":{required:false, default:()=>([])},
    "current":{},
    "selected":{},
    "mode":{type:String, required:true}
  },
  computed:{
    isDetailMode(){
      return this.mode === "detail";
    }
  },
};
</script>

