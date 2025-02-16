<template>
    <div class="content-box">
      <h1>{{ pokemon.name }}</h1>
  
      <img :src="pokemon.sprites.front_default" alt="Front Image">
  
      <section>
        <p>Height: {{ pokemon.height }}</p>
        <p>Weight: {{ pokemon.weight }}</p>
      </section>
    </div>
  </template>
  
  <script>
  import pokemonApiService from '../services/PokemonApiService.js';
  
  export default {
    created() {
      pokemonApiService.getDetailsByIdOrName(this.pokemonId)
        .then(response => {
          this.pokemon = response.data;
        });
    },
  
    computed: {
      pokemonId() {
        return this.$route.params.id;
      }
    },
  
    data() {
      return {
        pokemon: {}
      }
    }
  }
  </script>

  <style scoped>
    img {
      width: 100%;


    }

    section {
      display: flex;
      gap: 5rem;
    }



    


  </style>