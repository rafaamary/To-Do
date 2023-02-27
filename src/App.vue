<template>
  <main class="columns is-gapless is-multiline" style=background-color:#F9F5E7>
    <div class="column is-one-quarter">
      <BarraLateral> </BarraLateral>
    </div>
    <div class="column is-three-quarter">
      <FormularioTarefa @aoSalvartarefa="salvarTarefa"> </FormularioTarefa>
      <!-- Lista de Tarefas -->
      <div class="listaTarefas" v-for="(tarefa, index) in tarefas" :key="index">
        <TarefaLista  :tarefa="tarefa" @aoRemover="aoRemoverTarefa(index)"></TarefaLista>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import FormularioTarefa from "./components/FormularioTarefa.vue";
import TarefaLista from "./components/TarefaLista.vue";
import ITarefa from "./interfaces/ITarefa";

export default defineComponent({
    name: "App",
    components: {
      BarraLateral,
      FormularioTarefa,
      TarefaLista
    },
    data () {
      return {
        tarefas: [] as ITarefa[]
      }
    },
    methods: {
      salvarTarefa (tarefa: ITarefa) {
        this.tarefas.push(tarefa)
      },
      aoRemoverTarefa(index: number) {
        this.tarefas.splice(index, 1)
      }
    }
});
</script>

<style>
.listaTarefas {
  padding: 1.25rem;
}
</style>
