<template>
  <div class="w-full h-screen flex justify-center items-center">
    <h1 id="typewriter" class="text-4xl font-bold">{{ typewriter }}</h1>
  </div>
</template>
<script setup>
import { ref } from "vue";
const words = ["Beauty Products", "Healthcare Products", "Lab Test", "Medicines Products"];
let i = 0;
let j = 0;
let currentWord = "";
let isDeleting = false;
const typewriter = ref(null);

function type() {
  currentWord = words[i];
  if (isDeleting) {
    typewriter.value = currentWord.substring(0, j - 1);
    j = j - 1;
    if (j == 0) {
      isDeleting = false;
      i = i + 1;
    }
    if (i == words.length) {
      i = 0;
    }
  } else {
    typewriter.value = currentWord.substring(0, j + 1);
    j = j + 1;
    if (j == currentWord.length) {
      isDeleting = true;
    }
  }
  setTimeout(type, 100);
}

type();
</script>
