<template>
    <button class="button"  style="width:3rem;height:3rem" @click="marcarComCheck">
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
        if (this.check == true) {
          this.check = false;
        } else {
          this.check = true;
        }
      },
    }
});
</script>


