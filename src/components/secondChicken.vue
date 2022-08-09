<template>
  <div id="second-chicken">
    <div class="chicken2" :class="currColor">
      <div class="nest2"></div>
        <div id="second-egg" @click="checkIfCorrect"></div>
    </div>
  </div>
</template>
 
<script>

export default {
  name: "second-chicken",
  components: {

  },
  data() {
    return {
      chickenColors: ["red", "green", "blue", "purple", "red"],
      currColor: "",
      collected: 0
    }
    
  },
  mounted() {
    this.changeChicken();
    setInterval(this.changeChicken, Math.random()*1500 + 500);
  },
  methods: {
    changeChicken() {
      this.currColor = this.chickenColors[Math.round(Math.random() * 4)];
    },
    checkIfCorrect() {
      if(this.currColor === "red") {
        this.collected++;
        this.$emit("collect");
      } else {
        if(this.collected > 0) {
          this.collected--;
          this.$emit("wrong");
        }
        
      }
    }
  }
}
</script>

<style scoped> 
html,
body {
  margin: 0;
}

.red {
  background-image: url("../assets/media/redChicken.png");
}

.green {
  background-image: url("../assets/media/greenChicken.png");
}

.blue {
  background-image: url("../assets/media/blueChicken.png");
}

.purple {
  background-image: url("../assets/media/purpleChicken.png");
}
.chicken2 {
  width: 20vw;
  height: 20vh;
  background-size: 100% 100%;
  padding-right: 8vw;
  padding-left: 8vw;
}

.nest2 {
  background-image: url("../assets/media/chickenNest.png");
  width: 50vw;
  height: 30vh;
  background-size: 100% 100%;
  position: relative;
  top: 15%;
  right: 90%
}

#second-egg {
  background-image: url("../assets/media/egg.svg");
  background-size: 100% 100%;
  width: 10vw;
  height: 10vh;
  z-index: 4;
  top: -105%;
  left: 32%;
  position: relative;
}

</style>