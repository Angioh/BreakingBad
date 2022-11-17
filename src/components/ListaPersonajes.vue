<template>
 <div class=" text-center">    
  
  
  <div class=" table text-center h-20 w-0">
    <b class="italic">Lista Personajes</b>
    <div v-if="loading">
    <img src="../assets/loading.gif"/>
  </div>
  
    <div
      
    v-if="busqueda != ''"
      v-for="personaje in listaFiltrada"
    >
      <Personajes :personaje="personaje"
      @personajeFav="addFav" />
    
    </div>
  </div>
  <div class="pl-1 text-center"
  v-if="listaFav!=0">
    <b class="italic">Lista Favoritos</b>
    <div
      
      v-for="personaje in listaFav"
    >
      <PersonajeFav :fav="personaje"
      @elimFav="deleteFav" />
    </div></div>
</div>
</template>

<script>
import axios from "axios";
import Buscar from "./Buscar.vue";
import Personajes from "./Personajes.vue";
import PersonajeFav from "./PersonajeFav.vue";

export default {
  components: {
    Buscar,
    Personajes,
    PersonajeFav

  },
  props: {
    busqueda: {
      type: String,
      required: true,
    },

  },
  data() {
    return {
      lista: null,
      listaFav: [],
      recibo: false,
      loading:true,
      
    };
  },
  methods: {
    addFav(data){
      if(!this.listaFav.includes(data)){
        this.listaFav.push(data);
        this.guardadoLocal();
      } else {
        return null}
      
    },
    deleteFav(data){
        this.favs = this.favs.filter((el) => el !== data);
    },
  },
  created() {
    axios
      .get("https://www.breakingbadapi.com/api/characters")
      .then((result) => {
        this.lista = result.data;
        this.loading = false;
      });
  },
  computed: {
    listaFiltrada() {
      this.loading =false;
      return this.lista.filter((el) => {
        return el.name.toLowerCase().includes(this.busqueda.toLowerCase());
        
      });
    },
  },
};
</script>

<style lang="scss" scoped></style>
