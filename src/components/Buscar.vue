<template>
  <div>
    <p>
      Estamos buscando a <b>{{ entrada }}</b>
    </p>
    <input
      ref="input"
      id="personaje"
      type="text"
      @keydown.enter="enviar"
      v-model="entrada"
      placeholder="Personaje"
    />
  </div>
</template>

<script>
export default {
  name: "Buscar",
  emits: ["enviar"],
  data() {
    return {
      entrada: "",
    };
  },
  methods: {
    enviar() {
      this.$emit("enviar", this.entrada);
    },
  },
};
</script>

<style lang="scss" scoped></style>
