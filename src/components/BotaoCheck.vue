<template>
    <button class="button" @click="marcarComCheck">
      <span v-if="check" class="icon">
        <i class="fa-solid fa-check"></i>
      </span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: "BotaoCheck",
    data() {
        return {
            check: false
        }
    },
    methods: {
      marcarComCheck () {
        this.check = true;
      },
    }
});
</script>
