<template>
  <h1 v-if="!pokemonCorrecto">Espere por favor...</h1>
  <div v-else>
    <h1>Juego Pokemon</h1>
    <PokemonImg :pokemonId="pokemonCorrecto.id" :muestraPokemon="showPokemon" />

    <PokemonOps
      :opciones="arreglo"
      v-on:seleccionado="revisarSeleccion($event)"
    />
  </div>
</template>

<script>
import PokemonImg from "../components/PokemonImg.vue";
import PokemonOps from "../components/PokemonOps1.vue";
import obtenerFachadaPokemon from "../helpers/clientePokemonAPI";

export default {
  data() {
    return {
      arreglo: [],
      pokemonCorrecto: null,
      showPokemon: false,
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
      const indicePokemon = Math.floor(Math.random() * 4);
      this.pokemonCorrecto = this.arreglo[indicePokemon];
      this.showPokemon=false
      
    },
    revisarSeleccion(idSeleccionado) {
      console.log("evento en el padre");

      if (this.pokemonCorrecto.id == idSeleccionado) {
        //setTimeout(this.showPokemon, 5000, true)
        this.showPokemon = true;
        //this.cargaJuegoInicial()

      }
      console.log(idSeleccionado);
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