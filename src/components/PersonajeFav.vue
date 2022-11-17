<template>
    <div class="bg-green-600 box-content h-30 w-28 border-2 border-green-700 p-4 m-2 rounded-lg sm-text-center">
        <img :src="fav.img" class="h-70 w-80" /> <br />
      <b class="italic text-lg text-center">{{ fav.name }}</b><br />
      <b class="italic">Estado: <br/></b>
      <p>{{ fav.status }}</p>
      <b class="italic">Interpretado por: <br/></b>
      <p>{{ fav.portrayed }}</p>
      
      <button
          class="text-black rounded bg-green-700  px-4 mb-0 mt-7 border border-green-700 hover:bg-green-500"
         @click="elimFav"
        >
          Delete Fav
        </button>
    </div>
</template>

<script>
    export default {
        props:{
            fav:{
                type:null,
            }
        },
        emits:["elimFav"],
        methods:{
            elimFav(){
                this.$emit("elimFav",this.fav);
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>