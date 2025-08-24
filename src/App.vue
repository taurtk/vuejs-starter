<script setup>
import { items } from "./movies.json";
import { reactive } from "vue";
import { StarIcon } from "@heroicons/vue/24/solid";

let movies = reactive({ items });
console.log(movies);

// Toggle star for a specific movie
const toggleRating = (movie, n) => {
  // If clicked star is the current rating, reset to 0
  movie.rating = movie.rating === n ? 0 : n;
  console.log(`Movie "${movie.name}" new rating:`, movie.rating);
};
</script>

<template>
  <div class="p-4 bg-[#0c0d4eff] flex">
    <ul class="flex">
      <li v-for="movie in movies.items" :key="movie.id" class="mb-6">
  <h2>{{ movie.name }}</h2>
  <p>{{ movie.description }}</p>

  <!-- Container for image + overlay text -->
  <div style="position: relative; display: inline-block;">
    <img :src="movie.image" style="width: 400px; height: auto;" />
   <span
  style="
    position: absolute;
    top: 5px;
    right: 5px;
    color: white;
    background: rgba(0,0,0,0.6);
    padding: 2px 6px;
    border-radius: 4px;
    display: flex;
    align-items: center;
    gap: 4px;
  "
>
  <template v-if="movie.rating">
    <StarIcon class="h-5 w-5 text-yellow-500" />
    <span>{{ movie.rating }}</span>
  </template>
  <template v-else>
    --
  </template>
</span>

  </div>

  <p>Rating: {{ movie.rating }}</p>

  <ul class="flex">
    <li v-for="n in 5" :key="n">
      <button @click="toggleRating(movie, n)" class="p-1">
        <StarIcon
          class="inline h-6 w-6"
          :class="n <= movie.rating ? 'text-yellow-500' : 'text-gray-500'"
        />
      </button>
    </li>
  </ul>

  <ul class="flex gap-2 mt-1">
    <li
      v-for="genre in movie.genres"
      :key="genre"
      class="px-2 py-1 bg-gray-700 rounded"
    >
      {{ genre }}
    </li>
  </ul>
</li>

    </ul>
  </div>
</template>
<!-- 
<script setup>
import {ref} from 'vue'
const activeClass = ref('active')
const errorClass = ref('text-danger')
</script>

<template>
  <div :class="[activeClass, errorClass]">Hello World!</div>
</template> -->
