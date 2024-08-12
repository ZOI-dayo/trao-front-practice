<script setup lang="ts">
import { ref, watch } from 'vue'
import Pokemon from '../types/pokemon'
import axios, {AxiosResponse} from 'axios'
import PokemonCard from '../components/PokemonCard.vue'

// defineProps<{ begin: number, end:number }>()
const begin = ref<number>(2)
const end = ref<number>(5)

const baseUrl = 'https://m-api-prac.trap.show'
const pokemons = ref<Pokemon[]>([])
const updateCard = async () => {
  return (await axios.get(baseUrl + '/pokemon', {
    params: {
      startIndex: begin.value,
      endIndex: end.value
    }
  })).data as Pokemon[]
}
updateCard().then((data) => {
  pokemons.value = data
})
watch([begin, end], async ([begin, end]) => {
  pokemons.value = await updateCard()
})
</script>

<template>
  <h1> ポケモン図鑑 </h1>
  <div>
  <input type="number" v-model="begin" min="0" max="8" />
  <input type="number" v-model="end" min="0" max="8" />
  </div>
  <PokemonCard v-for="(pokemon, index) in pokemons" :key="pokemon.JpName" :no="begin+index" :pokemon="pokemon">
  </PokemonCard>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
