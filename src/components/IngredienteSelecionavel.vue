<script lang="ts">
import Tag from "@/components/Tag.vue";

export default {
  methods: {
    handleIngredienteClick() {
      this.selecionado = !this.selecionado
      this.$emit(this.selecionado ? "adicionar-ingrediente" : "remover-ingrediente", this.ingrediente);
    }
  },
  emits: ['adicionar-ingrediente', 'remover-ingrediente'],
  components: {Tag},
  props: {
    ingrediente: {type: String, required: true}
  },
  data() {
    return {
      selecionado: false
    }
  }
}
</script>

<template>
  <button class="ingrediente"
          @click="handleIngredienteClick"
          :aria-pressed="selecionado">
    <Tag :texto="ingrediente" :ativa="selecionado"/>
  </button>
</template>
<style scoped>
.ingrediente {
  cursor: pointer;
}
</style>