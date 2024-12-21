<template>
  <img :src="imagen" alt="No se puede ver" />
  <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
  <p>Recuerda que cuando finalices tu pregunta dar un ?</p>

  <h1>{{ pregunta }}</h1>
  <h2>{{ respuesta }}</h2>
</template>

<script>
export default {
  data() {
    return {
      //dentro del return se pone las propiedades reactivas
      pregunta: "Hola Mundo",
      respuesta: null,
      imagen:
        "https://yesno.wtf/assets/yes/14-b57c6dc03aa15a4b18f53eb50d6197ee.gif",
    };
  },
  watch: {
    pregunta(value, oldValue) {
      //value es el valor actual y oldValue es el valor anterior
      //   console.log(value);
      // console.log(oldValue);
      if (value.includes("?")) {
        //Programar la llamada a la API para obtener
        //el SI o el NO, y la imagen
        console.log("Llamada a la API");
        this.fachada();
      }
    },
  },
  methods: {
    async llamarAPI() {
      const data = await fetch("https://yesno.wtf/api").then((resp) =>
        resp.json()
      ); //await es para esperar de la respuesta de la API
      this.respuesta = data.answer;
      this.imagen = data.image;
      console.log(data);
    },
     async fachada() {//Cuando se necesita llamar desde otro metodo siempre se debe poner await y async
       await this.llamarAPI();
    },
  },
};
</script>

<style>
</style>