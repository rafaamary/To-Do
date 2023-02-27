<template>
  <div class="box has-text-weight-bold">
    <div class="columns is-flex is-align-items-center is-justify-content-space-between">
      <div class="column is-11">{{ tarefa.descricao }}</div>
      <BotaoCheck></BotaoCheck>
      <BotaoTrash :tarefa="tarefa" @aoRemover="removerTarefa"></BotaoTrash>
    </div>
  </div>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent , PropType} from 'vue';
import BotaoCheck from './BotaoCheck.vue';
import BotaoTrash from './BotaoTrash.vue';

export default defineComponent({
    name: 'TarefaLista',
    components: {
      BotaoCheck,
      BotaoTrash
    },
    props: {
      tarefa: {
        type: Object as PropType<ITarefa>,
        required: true
      }
    },
    methods: {
      removerTarefa(index: number) {
        this.$emit('aoRemover', index)
      }
    }
})
</script>

<style scoped>
.box {
  background: #F8EAD8;
}
</style>