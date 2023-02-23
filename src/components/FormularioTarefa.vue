<template>
  <div class="box formulario">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulario para criação de uma tarefa"
      >
        <input type="text" class="input" placeholder="Escreva sua tarefa" v-model="descricao"/>
      </div>

      <div class="column">
        <BotaoAdicionar @aoAdicionar="adicionarNovaTarefa" v-bind:disabled="botaoDesabilitado"></BotaoAdicionar>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BotaoAdicionar from "./BotaoAdicionar.vue";

export default defineComponent({
  name: "FormularioTarefa",
  emits: ['aoSalvartarefa'],
  data() {
    return {
      descricao: '',
    };
  },
  components: {
    BotaoAdicionar,
  },
  computed: {
    botaoDesabilitado(): boolean {
      return this.descricao.trim() === '';
    }
  },
  methods: {
    adicionarNovaTarefa(): void {
      this.$emit('aoSalvartarefa', {
        descricao: this.descricao,
      })
      this.descricao = ''
    },
  },
});
</script>

<style>
.formulario {
  color: var(--texto-primario);
  background-color: var(--bg-primario);
}
</style>