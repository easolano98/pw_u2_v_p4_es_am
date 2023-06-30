<template>
  <h1>Juego Pokemon</h1>
  <PokemonImg :pokemonId="151" :muestraPokemon="false" />

  <PokemonOps :opciones="arreglo" />
</template>

<script>
import PokemonImg from "../components/PokemonImg.vue";
import PokemonOps from "../components/PokemonOps1.vue";
import obtenerFachadaPokemon from "../helpers/clientePokemonAPI";

export default {
  data(){
    return{
       arreglo: []
    };
      
  },

  components: {
    PokemonImg,
    PokemonOps,
  },
  methods: {
    async cargaJuegoInicial() {
      const arregloPokemons = await obtenerFachadaPokemon();
      console.log(arregloPokemons);
      this.arreglo = arregloPokemons;
    },
  },
  mounted() {
    console.log("Se monto el componente");
    this.cargaJuegoInicial();
  },
};
</script>

<style>
</style>