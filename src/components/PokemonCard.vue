<script setup lang="ts">
import { ref } from 'vue'
import Pokemon from '../types/pokemon'

defineProps<{ no: number, pokemon: Pokemon }>()
</script>

<template>
  <div class="pokemon-card">
    <h3 class="pokemon-card_jname"> {{ no }}. {{ pokemon.JpName }} </h3>
    <h4 class="pokemon-card_ename"> {{ pokemon.EnName }} </h4>
    <img class="pokemon-card_pic" :src="pokemon.ImgUrl" :alt="pokemon.JpName" />
    <p class="pokemon-card_desc"> {{ pokemon.FlavorText }} </p>
  </div>
</template>

<style scoped>
.pokemon-card {
  font-family: 'DotGothic16', sans-serif;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  margin: 10px;
  width: 300px;
  height: 100%;
  display: inline-block;
}
.pokemon-card_jname {
  text-align: center;
  font-size: 2em;
  font-weight: 700;
  margin: 0;
}
.pokenon-card_ename {
  text-align: center;
  font-size: 1.2em;
  font-weight: 500;
  margin: 0;
}
.pokemon-card_pic {
  width: 150px;
  height: 150px;
  margin: 10px auto;
}
.pokemon-card_desc {
  font-size: 1em;
  margin: 0;
  text-align: left;
}
</style>
