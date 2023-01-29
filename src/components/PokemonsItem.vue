<script setup>
import axios from 'axios';
import { ref }  from 'vue';

import PokemonCard from './PokemonCard.vue';

const pokemons = ref([]);

const getPokemons = async ( ) => {
    try{
       const {data} = await axios.get('https://pokeapi.co/api/v2/pokemon?limit=100')
       pokemons.value = data.results;
    }catch{
        console.log('Parece que algo salio mal');
    }
}

getPokemons();

</script>

<template>
  <PokemonCard 
  v-for="(item) in pokemons"
  :key="item.name"
  :name="item.name"
  />
</template>
