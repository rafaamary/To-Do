<template>
  <div class="box has-text-weight-bold">
    <div class="columns is-flex is-align-items-center is-justify-content-space-between">
      <div class="column is-7">{{ tarefa.descricao }}</div>
      <BotaoCheck></BotaoCheck>
    </div>
  </div>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent , PropType} from 'vue';
import BotaoCheck from './BotaoCheck.vue';

export default defineComponent({
    name: 'TarefaLista',
    components: {
      BotaoCheck
    },
    props: {
      tarefa: {
        type: Object as PropType<ITarefa>,
        required: true
      }
    },
})
</script>

<style scoped>
.box {
  background: #FFD6EC;
}
</style>