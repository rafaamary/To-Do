<template>
  <button class="button" @click="adicionarTarefa">
    <span class="icon">
      <i class="fa-solid fa-plus"></i>
    </span>
    <span>Adicionar</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: "BotaoAdicionar",
    emits: ['aoAdicionar'],
    methods: {
    adicionarTarefa () {
      this.$emit('aoAdicionar')
    },
  }
})
</script>