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
    <img :src="require('./assets/bg2.jpg')">
    <div class="hidder">
      <vue-scratchable v-slot="{ init }" :brushOptions="brush" :hideOptions="hide" :onClick="() => { startConfetti(); clickOn1(); }"
        :onRelease="stopConfetti">
        <img :src="require('./assets/bg.jpg')" @load="init">
      </vue-scratchable>
      <div class="text" :style="hidder1">Grattez ici</div>
    </div>
    <div class="hidder-2">
      <vue-scratchable v-slot="{ init }" :brushOptions="brush" :hideOptions="hide" :onClick="() => { startConfetti(); clickOn2(); }"
        :onRelease="stopConfetti">
        <img :src="require('./assets/bg.jpg')" @load="init">
      </vue-scratchable>
      <div class="text" :style="hidder2">Grattez ici</div>
    </div>
  </div>
</template>

<script>
import VueScratchable from './components/vue-scratchable.vue';
// import paperPattern from './assets/natural-paper-texture.jpg';

VueScratchable.__defaults;

export default {
  components: {
    VueScratchable,
  },
  data() {

    let particleStarted = false

    // this.$confetti.update({
    //       defaultColors: [
    //         'red',
    //       ],
    // });

    const startConfetti = () => {
      if (!particleStarted) {
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
      haveCliked1: false,
      haveCliked2: false,
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
  computed: {
    hidder1(){
      return `display: ${this.haveCliked1 ? "none" : "flex"}`;
    },
    hidder2(){
      return `display: ${this.haveCliked2 ? "none" : "flex"}`;
    }
  },
  methods:{
    clickOn1(){
      this.haveCliked1 = true
    },
    clickOn2(){
      this.haveCliked2 = true
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0px;
}

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

.card {
  background-color: white;
  border-radius: 1.5rem;
  box-shadow: 10px 10px 5px rgb(0.6, 0.6, 0.6);
  width: 60%;
  aspect-ratio: 16/11;
  overflow: hidden;
  position: relative;
}

.card>img {
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
  width: 30%;
  height: 30%;
  background: rgba(0.9, 0.9, 0.9, 0.5);
  transform: translate(-50%, -50%);
  top: 30%;
  left: 24%;
}

.text {
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  transform: translateY(-100%);
  pointer-events: none;
  animation: text-animation 1s ease-in-out 0s infinite alternate;
}

@keyframes text-animation{
  0% {
    transform: translateY(-100%) scale(1);
  }
  100% {
    transform: translateY(-100%) scale(1.2);
  }
}

.hidder-2 {
  position: absolute;
  display: block;
  width: 13%;
  height: 12%;
  background: rgba(0.9, 0.9, 0.9, 0.5);
  transform: translate(-50%, -50%);
  top: 50%;
  left: 50%;
}

.vue-scratchable-wrapper {
  width: 100%;
  height: 100%;
  position: relative;
}

.vue-scratchable-wrapper>img {
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
