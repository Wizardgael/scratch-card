<template>
  <div class="container">
    <img :src="require('./assets/bg.jpg')">
    <div class="hidder">
      <vue-scratchable v-slot="{ init }" :brushOptions="brush" :hideOptions="hide">
        <img :src="require('./assets/bg.jpg')" @load="init">
      </vue-scratchable>
    </div>
  </div>
</template>

<script>
import VueScratchable from './components/vue-scratchable.vue';
export default {
  components: {
    VueScratchable,
  },
  data() {
    return {
      percentage: 0,
      hide: {
        type: 'color',
        value: "#000"
      },
      brush: {
        size: 60,
        shape: 'round',
      },
    };
  },
}
</script>

<style>
html,
body {
  width: 100%;
  height: 100%;
  margin: 0;
  overflow: hidden;
}

#app {
  width: 100%;
  height: 100%;
  margin: 0;
}

.container {
  position: relative;
  display: inline;
}

.container>img {
  width: 100%;
  object-fit: contain;
  object-position: top;
  display: block;
}

.hidder {
  position: absolute;
  width: 20%;
  height: 11%;
  background: rgba(0.9, 0.9, 0.9, 0.5);
  transform: translate(-50%, -50%);
  top: 15.5%;
  left: 19%;
}

.vue-scratchable-wrapper {
  width: 100%;
  height: 100%;
}

.vue-scratchable-wrapper > img {
  opacity: 0;
}
</style>
