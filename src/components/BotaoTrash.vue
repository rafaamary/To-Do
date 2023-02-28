<template>
    <button class="button" style="width:3rem;height:3rem" @click="removerTarefa">
        <i class="fa-sharp fa-solid fa-trash"></i>
    </button>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BotaoTrash',
    props: {
      tarefa: {
        Object,
        required: true
      }
    },
    emits: ['aoRemover'],
    methods: {
    removerTarefa () {
      this.$emit('aoRemover', this.tarefa)
    },
  }
})
</script>