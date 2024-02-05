<script setup>
import c from "./keysnotes/C1.mp3";</script>
<script>
const playSound = () => {
  const audio = new Audio(c);
  audio.play();
};
</script>

<template>
  <div>
    <h1 class="text-3xl font-bold underline">Hello world!</h1>
    <div
      id="c-1-note"
      class="flex justify-center bg-blue-100 w-1/12 p-auto"
      @click="playSound"
    >
      c
    </div>
  </div>
</template>

<style scoped></style>
