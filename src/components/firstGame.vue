<template>
  <div id="firstGame">
    <div v-show="!isWearing">
      <img class="sunGlasses" src="../assets/media/sunGlasses.png" @click="openSunGlass" @v-hammer:tap="$emit('next-page')"/>
      <img class="next" src="../assets/media/arrow.png" v-if="canContinue" @click="$emit('next-page')"/>
        <div class="collected">{{eggsCollected}}</div>
        <div class="lul">
          <first-chicken v-for="n in 6" class="chicken" :key="'chicken' + n" :id="'chicken' + n"></first-chicken>
        </div>
        <div class="eggs">
          <first-egg class="egg" v-for="n in 6" :key="n" :id="'egg' + n" @collected="addEgg" @collectedWrong="removeEgg"></first-egg>
        </div>
    </div>
    <div v-if="isWearing"> 
      <img class="sunGlasses" src="../assets/media/sunGlasses.png" @click="closeSunGlasses"/>
      <div class="lul">
        <first-chicken v-for="n in 6" class="chicken" :key="'chicken' + n" :id="'chicken' + n"></first-chicken>
      </div>
      <div class="dark-screen"></div>
      <img src="../assets/media/goldenEgg.svg" class="bitso" @click="bitsoCollected" v-show="!isBitso"/>
    </div>
  </div>
</template>
 
<script>
import firstChicken from '@/components/firstChicken.vue'
import firstEgg from '@/components/firstEgg.vue'
export default {
  name: "first-game",
  components: {
    firstChicken,
    firstEgg
  },
  data() {
    return {
      canContinue: false,
      numCollected: 0,
      isWearing: false,
      isBitso: false
    }
  },
  methods: {
    addEgg() {
      this.numCollected++;
      if (this.numCollected >= 2) {
        this.canContinue = true;
      }
    },
    removeEgg() {
      this.numCollected -= 1;
    },
    openSunGlass() {
      this.isWearing = true;
    },
    closeSunGlasses() {
      this.isWearing = false;
    },
    bitsoCollected() {
      this.isBitso = true;
      this.$emit("caught");
    }
  },
  computed: {
    eggsCollected() {
      return(`${this.numCollected}/15`);
    }
  }
}
</script>

<style scoped>
html,
body {
  margin: 0;
}

#firstGame {
  background-image: url("../assets/media/bg.png");
  background-size: 100% 100%;
  width: 100vw;
  height: 100vh;
}

.lul,
.eggs {
  position: absolute;
  transform: translate(-50%, -50%);
  display: flex;
  height: 80vh;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: stretch;
  z-index: 2;
}

.lul {
  top: 50%;
  left: 50%;
  width: 80vw;
}

.eggs {
  left: 53vw;
  width: 85vw;
  top: 58vh;
}

.egg {
  padding-right: 15vw;
  padding-left: 15vw;
}

.collected {
  color: white;
  font-size: 7vw;
  position: absolute;
  top: 2.5vh;
  left: 70vw;
}

.back,
.next {
  width: 10vw;
  height: 5vh;
  position: absolute;
  z-index: 5;
}

.back {
  top: 2vh;
  right: 4vw;
}

.next {
  top: 93vh;
  left: 4vw;
}

.sunGlasses {
  width: 20vw;
  height: auto;
  position: absolute;
  top: -0.5vh;
  left: 45vw;
  position: absolute;
  z-index: 3;
}

.bitso {
  width: 10vw;
  height: auto;
  position: absolute;
  top: 46vh;
  left: 25vw;
  z-index: 3;
}

.dark-screen {
  background-color: rgb(0, 0, 0, 0.4);
  width: 100vw;
  height: 100vh;
  position: absolute;
  z-index: 2;
}
</style>