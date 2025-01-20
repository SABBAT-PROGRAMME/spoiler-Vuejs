<!-- tamplate -->
<template>
  <h1>Hello World !</h1>

  <button @click="toggleSpoiler">
    {{ showSpoiler ? "Cacher le spoiler" : "Montrer le spoiler" }}
  </button>
  <div v-if="showSpoiler" class="spoiler">
    A la fin de la serie l'acteur principal meurt !
  </div>
</template>

<!-- script -->
<script setup>
import { ref } from "vue";

const showSpoiler = ref(false);
const toggleSpoiler = () => {
  showSpoiler.value = !showSpoiler.value;
};
</script>

<!-- style -->
<style>
.spoiler {
  padding: 1rem;
  border: 1px solid rgb(166, 198, 9);
  margin-top: 0.5rem;
}
</style>
