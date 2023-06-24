<template>
  <img v-if="urlImagen" :src="urlImagen" alt="no se puede mostrar imagen" />
  <div class="dg_dark"></div>
  <div class="contenedor">
    <h1>Caracola Mágica</h1>
    <input v-model="preguntaInput" type="text" placeholder="Preguntame" />
    <p>Recuerda terminar con un ? la pregunta</p>
    <div>
      <h2>{{ pregunta }}</h2>
      <h1>{{ respuesta || "YES/NO" }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pregunta: "",
      preguntaInput: "",
      respuesta: "",
      urlImagen: null,
    };
  },
  methods: {
    async consumirApi() {
      const { answer, image } = await fetch("https://yesno.wtf/api").then((r) =>
        r.json()
      );
      console.log(answer);
      console.log(image);
      this.respuesta = answer;
      this.urlImagen = image;
    },
  },
  watch: {
    preguntaInput(value, oldValue) {
      console.log(value);
      console.log(oldValue);
      
      if (value.includes("?")) {
        this.pregunta = this.preguntaInput
        this.preguntaInput = ""
        this.respuesta = "Pensando..."
        console.log("consumir el API");
        this.consumirApi();
      }
    },
  },
};
</script>

<style>
img,
.dg_dark {
  height: 100vh;
  width: 100vw;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
}
.dg_dark {
  background-color: rgba(0, 0, 0, 0.445);
}
.contenedor {
  position: relative;
}
input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 10px;
  border: none;
  outline: none;
}
p,
h1,
h2 {
  color: aliceblue;
}
h1 {
  margin-bottom: 100px;
}
p {
  font-size: 25px;
  margin-top: 10px;
}
</style>