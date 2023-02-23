<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral> </BarraLateral>
    </div>
    <div class="column is-three-quarter">
      <FormularioTarefa @aoSalvartarefa="salvarTarefa"> </FormularioTarefa>
      <!-- Lista de Tarefas -->
      <div class="listaTarefas">
        <TarefaLista v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"></TarefaLista>
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
    }
});
</script>

<style>
.listaTarefas {
  padding: 1.25rem;
}
</style>
