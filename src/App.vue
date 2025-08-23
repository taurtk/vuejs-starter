<script setup>
import { items } from "./movies.json";
import {reactive} from 'vue';
/*
 This is an Icon that you can use to represent the stars if you like
 otherwise you could just use a simple ⭐️ emoji, or * character.
*/
import { StarIcon } from "@heroicons/vue/24/solid";
let movies  = reactive({items});
console.log(movies);
</script>

<template>
  <!-- This is where your template goes	-->
  <div>
    <ul>
      <li v-for="movie in movies.items" :key="movie.id">
        <h2>{{movie.name}}</h2>
        <p>{{movie.description}}</p>
        <img :src='movie.image'/>
        <p>Rating: {{movie.rating}}</p>
        <ul class="flex">
        <li v-for="n in movie.rating" :key="n">
          <StarIcon class="inline h-6 w-6 text-yellow-500"/>
       
      </li>
      <li v-for="genre in movie.genres" :key="genre">
        {{genre}}     
      </li>
       </ul>
       
      </li>
    </ul>
  </div>
</template>
