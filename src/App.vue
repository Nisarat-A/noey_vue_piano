<script setup>
import * as piano from "./piano.js";
import SvgName from "./components/icons/svgname.svg?raw";

const { getAudioPath, playSound, isBlackKey, keyBindings, handleKeyUp ,handleClick } = piano;

</script>
<template>
  <div>
    <div id="header" class="w-full h-20">
      <div class="svg-image flex justify-center mt-6" v-html="SvgName"></div>
    </div>

    <video autoplay muted loop class="video">
      <source src="./assets/pastelsea.mp4" type="video/mp4" />
      <source src="./assets/pastelsea.mp4" type="video/webm" />
    </video>

    <div
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
    </div>
    <div id="footer"></div>
  </div>
</template>
<style scoped>
@import "./components/util.css";
.piano-key {
  height: 120px;
  width: 40px;
  border: 1px solid #000;
  display: inline-block;
  text-align: center;
  line-height: 120px;
  cursor: pointer;
  user-select: none;
}
.black-key {
  background-color: black;
  color: white;
}
.piano-key:hover {
  background-color: lightgray;
}
</style>
