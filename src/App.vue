<template>
  <h1>Hello World !</h1>

  <button @click="toggleSpoiler" class="spoiler">
    {{ showSpoiler ? "Cacher le spoiler" : "Montrer le spoiler" }}
  </button>

  <FadeSlideTrasition>
    <div v-if="showSpoiler" class="spoiler">
      À la fin de la série, l'acteur principal meurt !
    </div>
  </FadeSlideTrasition>

  <hr />

  <form action="" role="group" @submit.prevent="addMovie">
    <input type="text" placeholder="Ajouter un film" v-model="movie" />
    <button :disabled="movie.length === 0">Ajouter</button>
  </form>

  <ul>
    <TransitionGroup name="list">
      <li v-for="(movie, index) in movies" :key="index">
        {{ movie }}
        <button @click="removeMovie(movie)" class="delete">X</button>
      </li>
    </TransitionGroup>
  </ul>
</template>

<script setup>
import { ref } from "vue";
import FadeSlideTrasition from "./FadeSlideTrasition.vue";

const showSpoiler = ref(false);
const toggleSpoiler = () => (showSpoiler.value = !showSpoiler.value);

const movie = ref("");
const movies = ref(["Titanic", "Un prince à New-York", "Avatar", "Matrix"]);

// methods

const addMovie = () => {
  movies.value.push(movie.value);
  movie.value = "";
};

const removeMovie = (movie) => {
  movies.value = movies.value.filter((m) => m !== movie);
};
</script>

<style>
.spoiler {
  padding: 1rem;
  border: 1px solid rgb(166, 198, 9);
  margin-top: 0.5rem;
  transition: 0.5s;
}

.delete {
  background-color: gray;
  border: none;
}

.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

/* .list-leave-active {
  position: absolute;
} */

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>
