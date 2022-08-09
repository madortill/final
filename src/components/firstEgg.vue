<template>
  <div id="firstEgg" :class="!noEgg ? '' : 'notVisible'">
    <div class="firstEgg" @click="checkIfCollected">
      <div class="timer">{{ timerOutput }}</div>
    </div>
  </div>
</template>
 
<script>

export default {
  name: "first-egg",
  props: ["egg-name"],
  data() {
    return {
      collected: 0,
      noEgg: true,
      timerSec: 0,
      timerMin: 0,
      timerInterval: "",
      timerOut: ""
    }
    
  },
  mounted() {
    setTimeout(this.startTimer, Math.random()*5000 + 1000);
  },
  methods: {
    startTimer() {
      this.noEgg = false;
      this.timerInterval = setInterval(this.timer, 100);
    },
    timer() {
      this.timerSec++;
      if (this.timerSec === 60) {
        this.timerMin++;
        this.timerSec = 0;
      }
      if (this.timerMin === 1 && this.timerSec === 10) {
        this.newEgg();
      }
    },
    newEgg() {
      this.noEgg = true;
      this.timerOut = setTimeout(() => {
        this.noEgg = false;
        this.timerSec = 0;
        this.timerMin = 0;
      }, Math.random() * 2000 + 1500);
      
    },
    checkIfCollected() {
      if(this.timerSec > 30 && this.timerMin === 0) {
        this.collected++;
        this.$emit("collected");
      } else {
        if(this.collected > 0) {
          this.collected--;
          this.$emit("collectedWrong");
        }
      }
      this.newEgg();
    }
  },
  computed: {
    timerOutput() {
      return(`${String(this.timerMin).padStart(2, "0")}:${String(this.timerSec).padStart(2, "0")}`)
    }
  }
}
</script>

<style scoped>
@font-face {
  font-family: "rubik";
  src: url("../assets/font/Rubik-Regular.ttf");
}

html,
body {
  margin: 0;
}

.firstEgg {
  background-image: url("../assets/media/egg.svg");
  background-size: 100% 100%;
  width: 10vw;
  height: 10vh;
}

.timer {
  position: relative;
  top: 44%;
  right: 70%;
  color: rgb(1, 16, 95);
  font-size: 3.6vw;
  text-shadow: 1px 1px white;
  font-family: "rubik";
}

.notVisible {
  opacity: 0;
}
</style>