<script setup>
import * as piano from "./piano.js";
const { getAudioPath, playSound, isBlackKey, keyBindings ,handleKeyUp } = piano;
</script>
<template>
  <div>
    <div id="animate-bg"></div>
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
      >
        {{ note }}
        <span> ({{ key }}) </span>
      </div>
    </div>
    <div id="footer"></div>
  </div>
</template>
<style scoped>
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
