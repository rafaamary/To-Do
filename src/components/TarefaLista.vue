<template>
  <div class="box has-text-weight-bold">
    <div class="columns is-flex is-align-items-center is-justify-content-space-between">
      <div v-if="!editando" class="column is-10">{{ tarefaLocal.descricao }}</div>
      <div v-if="editando" class="column is-10">
        <input type="text" class="input" placeholder="Editar Tarefa" v-model="descricao"/>
        <button class="button" @click="salvar" :disabled="descricao.trim() === '' || descricao === tarefaLocal.descricao">
          <span>Salvar</span>
        </button>
      </div>
      <BotaoCheck></BotaoCheck>
      <BotaoTrash :tarefa="tarefa" @aoRemover="removerTarefa"></BotaoTrash>
      <BotaoEditar @click="editar"></BotaoEditar>
    </div>
  </div>
</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent , PropType} from 'vue';
import BotaoCheck from './BotaoCheck.vue';
import BotaoTrash from './BotaoTrash.vue';
import BotaoEditar from './BotaoEditar.vue';

export default defineComponent({
    name: 'TarefaLista',
    emits: ['aoEditar', 'aoRemover'],
    components: {
      BotaoCheck,
      BotaoTrash,
      BotaoEditar,
    },
    props: {
      tarefa: {
        type: Object as PropType<ITarefa>,
        required: true
      }
    },
    data() {
      return {
        editando: false,
        descricao: this.tarefa.descricao,
        tarefaLocal: {...this.tarefa}
      }
    },
    methods: {
      removerTarefa(index: number) {
        this.$emit('aoRemover', index)
      },
      editar() {
        this.editando = true
      },
      salvar() {
        this.tarefaLocal.descricao = this.descricao.trim();
        this.$emit('aoEditar', this.tarefaLocal)
        Object.assign(this.tarefa, this.tarefaLocal)
        this.editando = false
      }
    }
})
</script>

<style scoped>
.box {
  background: #F8EAD8;
}
</style>