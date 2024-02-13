<script setup>
import * as piano from "./piano.js";
import SvgName from "./components/icons/svgname.svg?raw";
const {
  getAudioPath,
  playSound,
  isBlackKey,
  keyBindings,
  handleKeyUp,
  handleClick,
} = piano;
</script>
<template>
  <div>
    <header id="header" class="w-full h-20">
      <div class="svg-image flex justify-center mt-6" v-html="SvgName"></div>
    </header>

    <video autoplay muted loop class="video">
      <source src="./assets/pastelsea.mp4" type="video/mp4" />
      <source src="./assets/pastelsea.mp4" type="video/webm" />
    </video>

    <section
      id="piano"
      class="flex justify-center"
      @keyup="handleKeyUp"
      tabindex="0"
    >
      <div
        v-for="(note, key) in keyBindings"
        :key="key"
        :class="{ 'piano-key': true, 'black-key': isBlackKey(note) }"
        :data-note="note"
        class="rounded"
        @click="handleClick(note)"
      >
        {{ note }}
      </div>
    </section>
    <footer class="flex justify-center p-10">
      <p class="font-l font-light from-stone-500">
        @DAIISARA INT203 ClIENT SIDE II
      </p>
      
    </footer>
  </div>
</template>
<style scoped>
@import "./components/util.css";
.piano-key {
  width: 4.5vw;
  height: 30vh;
  display: inline-block;
  text-align: center;
  line-height: 270px;
  cursor: pointer;
  user-select: none;
  background-color: #ffff;
  color: black;
  font-size: 1vw; /* Responsive font size */
  border: 1px solid #000;
  border-radius: 8px;
}
.black-key {
  width: 3vw;
  z-index: 2;
  line-height: 20px;
  margin: 0 -1.8vw 0 -1.8vw;
  height: 15vh;
  border: 1px solid #000;
  border-radius: 0 0 5px 5px;
  background-color: #363636;
}
.piano-key:hover {
  background-color: lightgray;
}
</style>
