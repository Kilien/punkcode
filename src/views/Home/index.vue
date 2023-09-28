<script setup lang="ts">
import Sketch from "@/utils/module.js";
import { getImage } from "@/utils/tools";


onMounted(() => {
  new Sketch({
    dom: document.getElementById("container"),
    config: false,
    url: getImage('tree.jpg'),
    mouseover: "#mouseover",
    settings: {
      number: 5000,
      trails: 0.1,
      size: 0.9,
      gravity: 0.3,
      gravityDifference: 0.04,
      randomness: 0.9,
      sideScale: 10,
      speedScale: 10
    }
  });
})
</script>

<template>
  <div class="home-wrap">
    <a class="frame__enter" id="mouseover">enter</a>
    <div class="content" id="container"></div>
    <div class="over"></div>
  </div>
</template>

<style lang="scss" scoped>
.home-wrap {
  width: 100%;
  position: relative;

  a {
    text-decoration: none;
    color: #5f5f5f;
    outline: none;
  }

  a:hover {
    color: #000;
    outline: none;
  }

  /* Better focus styles from https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-visible */
  a:focus {
    /* Provide a fallback style for browsers
	 that don't support :focus-visible */
    outline: none;
    background: lightgrey;
  }

  a:focus:not(:focus-visible) {
    /* Remove the focus indicator on mouse-focus for browsers
	 that do support :focus-visible */
    background: transparent;
  }

  a:focus-visible {
    outline: 2px solid red;
    background: transparent;
  }

  .content {
    display: flex;
    flex-direction: column;
    width: 100vw;
    position: relative;
    align-items: center;
    height: 100vh;
    justify-content: center;
  }

  canvas {
    display: block;
  }

  .over {
    position: fixed;
    pointer-events: none;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background-position: 50% 50%;
    background-repeat: no-repeat;
    background-size: cover;
    opacity: 1;
    will-change: opacity;
  }
}
</style>
