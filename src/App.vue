<template>
  <!-- <div class="container">
    <img :src="require('./assets/bg.jpg')">
    <div class="hidder">
      <vue-scratchable v-slot="{ init }" :brushOptions="brush" :hideOptions="hide" :onClick="startConfetti" :onRelease="stopConfetti">
        <img :src="require('./assets/bg.jpg')" @load="init">
      </vue-scratchable>
    </div>
  </div> -->
  <div class="card">
    <img :src="require('./assets/bg.jpg')">
    <div class="hidder">
      <vue-scratchable v-slot="{ init }" :brushOptions="brush" :hideOptions="hide" :onClick="startConfetti" :onRelease="stopConfetti">
        <img :src="require('./assets/bg.jpg')" @load="init">
      </vue-scratchable>
    </div>
  </div>
</template>

<script>
import VueScratchable from './components/vue-scratchable.vue';

VueScratchable.__defaults;

export default {
  components: {
    VueScratchable,
  },
  data() {

    let particleStarted = false

    const startConfetti = () => {
      if(!particleStarted){
        this.$confetti.start()
        particleStarted = true
        console.log("start")
      }
    }

    const stopConfetti = () => {
      setTimeout(() => {
        this.$confetti.stop()
        particleStarted = false
        console.log("stop")
      }, 200)
    }


    return {
      startConfetti,
      stopConfetti,
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

* { margin: 0; padding: 0px; }

html,
body {
  width: 100%;
  height: 100%;
  margin: 0;
  overflow: hidden;
  background-color: #aaaaaa;
}

#app {
  width: 100%;
  height: 100%;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.card{
  background-color: white;
  border-radius: 1.5rem;
  box-shadow: 10px 10px 5px rgb(0.6, 0.6, 0.6);
  width: 90%;
  aspect-ratio: 16/9;
  overflow: hidden;
  position: relative;
}

.card > img {
  width: 100%;
  object-fit: contain;
  -o-object-fit: contain;
  object-position: center;
  -o-object-position: top;
  position: absolute;
}

.hidder {
  position: absolute;
  display: block;
  width: 20%;
  height: 11%;
  /* background: rgba(0.9, 0.9, 0.9, 0.5); */
  transform: translate(-50%, -50%);
  top: 15.5%;
  left: 19%;
}

.vue-scratchable-wrapper {
  width: 100%;
  height: 100%;
  position: relative;
}

.vue-scratchable-wrapper > img {
  opacity: 0;
}

/* .container {
  position: relative;
}

.container > img {
  width: 100%;
  object-fit: contain;
  -o-object-fit: contain;
  object-position: top;
  -o-object-position: top;
  display: block;
  position: relative;
}

.hidder {
  position: absolute;
  display: block;
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
  position: relative;
}

.vue-scratchable-wrapper > img {
  opacity: 0;
} */
</style>
