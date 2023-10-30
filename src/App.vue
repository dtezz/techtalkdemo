<script setup>
import { ref, reactive } from 'vue'
const counter = reactive({ count: 0 })
const message = ref('Demo!')
const pokemon = reactive({ name: '', image: '' })

// function increment() {
//   counter.count++
// }

const pokeLink = 'https://pokeapi.co/api/v2/pokemon/psyduck/'
const getPokemon = async () => {
  const res = await fetch(pokeLink)
  const data = await res.json()
  pokemon.name = data.name
  pokemon.image = data.sprites.other['official-artwork'].front_default
}
</script>

<template>
  <h1>{{ message }}</h1>
  <button v-on:click="getPokemon">Click me to get a pokemon</button>
  <p>this pokemon is {{ pokemon.name }}</p>
  <img v-if="pokemon.image" :src="pokemon.image" />
</template>
