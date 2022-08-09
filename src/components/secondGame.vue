<template>
  <div id="second-game">
    <img class="next" src="../assets/media/arrow.png" @click="$emit('next-page')" v-if="checkIfCan"/>
    <div>+</div>
    <div>-</div>
    <div class="collected">{{eggsCollected}}</div>
    <div class="lul">
      <second-chicken v-for="n in 6" class="chicken" :key="'chicken' + n" :id="'chicken' + n" @collect="numEggsCollected++" @wrong="numEggsCollected--"></second-chicken>
    </div>
  </div>
</template>
 
<script>
import secondChicken from '@/components/secondChicken.vue'
export default {
  name: "second-game",
  components: {
    secondChicken
  },
  data() {
    return {
      numEggsCollected: 0,
    }
    
  },
  methods: {
  },
  computed: {
    eggsCollected() {
      return(`${this.numEggsCollected}/15`);
    },
    checkIfCan() {
      return(this.numEggsCollected >= 2 ? true: false);
    }
  }
}
</script>

<style scoped> 
html,
body {
  margin: 0;
}

#second-game {
  background-image: url("../assets/media/bg.png");
  background-size: 100% 100%;
  width: 100vw;
  height: 100vh;
}

.lul {
  top: 50%;
  left: 50%;
  width: 80vw;
  position: absolute;
  transform: translate(-50%, -50%);
  display: flex;
  height: 80vh;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: stretch;
  z-index: 2;
}

.back,
.next {
  width: 10vw;
  height: 5vh;
  position: absolute;
  z-index: 6;
}

.back {
  top: 2vh;
  right: 4vw;
}

.next {
  top: 93vh;
  left: 4vw;
}

.collected {
  color: white;
  font-size: 7vw;
  position: absolute;
  top: 2.5vh;
  left: 60vw;
}

</style>