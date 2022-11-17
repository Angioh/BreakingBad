<template>
    <div class="bg-green-600 box-content h-65 w-38 border-2 border-green-700 p-4 m-2 rounded-lg sm-text-center font-Roboto">
        <img :src="personaje.img" class="h-70 w-80" /> <br />
      <b>{{ personaje.name }}</b><br/>
      <b class="italic">Fecha de nacimiento: </b>
      <p>{{ personaje.birthday }}</p>
      <b class="italic">Alias: </b>
      <p>{{ personaje.nickname }}</p>
      <b class="italic">
        Trabajo/ocupaciones:<br /></b>
        <li v-for="ocuppation, index in this.personaje.occupation" :key="index">
                    {{ ocuppation }}
                </li>
      <button
          class="text-black rounded bg-green-700  px-4 mb-0 mt-7 border border-green-700 hover:bg-green-500"
          @click="personajeFav"
        >
          Add Fav
        </button>
    </div>
</template>

<script>
    export default {
        components:{
        },
        props:{
            personaje:{
                type: Object,
            }
        },
        emits:["personajeFav"],
        methods:{
            personajeFav(){

                this.$emit("personajeFav",this.personaje);
            },
       
    }};
</script>

<style lang="scss" scoped>

</style>