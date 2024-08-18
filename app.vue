<script lang="ts" setup>
import { useFullscreen } from "@vueuse/core";
const panoLocation = ref(null);
const panoContainer = ref(null);
const { isFullscreen, enter, exit, toggle } = useFullscreen(panoContainer);
</script>

<template>
  <div class="article">
    <h1>I am an Aframe test</h1>
    <button @click="panoLocation = 'pano.html'">load iframe</button>
    <button @click="toggle">toggle fullScreen</button>

    <div class="panoContainer" ref="panoContainer">
      <button v-if="isFullscreen" class="exit" @click="exit">
        exit fullScreen
      </button>
      <iframe :src="panoLocation" />
    </div>
  </div>
</template>

<style>
.panoContainer {
  position: relative;
  width: 900px;
  aspect-ratio: 4/3;
}
.article {
  position: relative;
}
iframe {
  width: 100%;
  height: 100%;
  z-index: 1;
}
.exit {
  position: absolute;
  top: 0;
  left: 50%;
  z-index: 99999999999;
}
</style>
