<template>
  <h1>Juego Pokemon</h1>
  <PokemonImg
    v-if="correcto != 0"
    :pokemonId="correcto"
    :muestraPokemon="mostrarImagen"
  />

  <PokemonOps v-if="correcto != 0" :opciones="arreglo" :correcto="correcto" @verificarVictoria="recibirDato"/>
</template>

<script>
import PokemonImg from "../components/PokemonImg.vue";
import PokemonOps from "../components/PokemonOps1.vue";
import obtenerFachadaPokemon from "../helpers/clientePokemonAPI";

export default {
  data() {
    return {
      arreglo: [],
      correcto: 0,
      mostrarImagen: false,
    };
  },

  components: {
    PokemonImg,
    PokemonOps,
  },
  methods: {
    async cargaJuegoInicial() {
      const arregloPokemons = await obtenerFachadaPokemon();
      //console.log(arregloPokemons);
      this.arreglo = arregloPokemons;

      this.elegirCorrecto();
    },
    elegirCorrecto() {
      const n = Math.floor(Math.random() * this.arreglo.length);

      this.correcto = this.arreglo[n].id;
      console.log(this.correcto);
    },
    recibirDato(dato){
      this.mostrarImagen = dato
    }
  },
  mounted() {
    console.log("Se monto el componente");
    this.cargaJuegoInicial();
  },
};
</script>

<style>
</style>