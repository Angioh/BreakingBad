<template >
  <div class="bg-gradient-to-b from-green-400 to-green-900 min-h-screen">
    <div class="flex justify-center">
    <img src="./assets/bb.jpg" class="place-content-center w-50 h-50"/>
  </div>
  <div class=" flex justify-center">
      <Buscar @enviar="recibir" class="justify-center pb-4 pt-4" /><br />
    </div>
  <ListaPersonajes :busqueda="busqueda" class="flex justify-center"/>
</div>
</template>

<script>
import ListaPersonajes               from "./components/ListaPersonajes.vue";
import Buscar from "./components/Buscar.vue";
export default {
  components: {
    ListaPersonajes,
    Buscar,
  },
  name: "App",
  data() {
    return {
      busqueda: "",
    };
  },
  methods: {
    recibir(nuevaBusqueda) {
      this.busqueda = nuevaBusqueda;
    },
  },
};
</script>

<style scoped></style>
