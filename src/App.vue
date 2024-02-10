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

<script setup>

const getAudioPath = (note) => {
  const path = `./src/piano-mp3/${note}.mp3`;
  console.log("Audio Path:", path);
  return path;
};

const playSound = (note) => {
  const audioPath = getAudioPath(note);
  const audio = new Audio(audioPath);
  audio.play();
  console.log("Audio played successfully");
};

const isBlackKey = (note) => {
  const blackKeys = ["Bb", "Db", "Eb", "Gb", "Ab"];
  return blackKeys.includes(note.substring(0, 2));
};

const keyBindings = {
  "A": "A3",
  "S": "Bb3",
  "D": "B3",
  "F": "C4",
  "G": "Db4",
  "H": "D4",
  "J": "Eb4",
  "K": "E4",
  "L": "F4",
  ";": "Gb4",
  "'": "G4",
  "Z": "Ab4",
  "X": "A4",
  "C": "Bb4",
  "V": "B4",
  "B": "C5",
  "N": "Db5",
  "M": "D5",
  ",": "Eb5",
  ".": "E5",
  "/": "F5",
  "Q": "Gb5",
  "W": "G5",
  "E": "Ab5",
  "R": "A5",
};

const handleKeyUp = (event) => {
  const key = event.key.toUpperCase();
  if (keyBindings[key]) {
    playSound(keyBindings[key]);
  }
};
</script>

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
