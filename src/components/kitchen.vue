<template>
  <div id="kitchen">
    <div class="meet" v-if="!isCooking && !checkIfCaught">
      <img src="../assets/media/eggInJail.png" class="jail" :class="clicked ? 'jailAni': ''"/>
      <img src="../assets/media/goldenEgg.svg" class="bitso" :class="clicked ? 'bitsoAni': ''"/>
      <div v-if="!clicked">
        <img src="../assets/media/speechBubble.png" class="speech-bub"/>
        <div class="main-txt">כבר חשבתי שלא תגיע... הבאת את הכסף?</div>
        <button class="yes-btn" @click="nextScreen">כן</button>
      </div>
      <div class="black-screen" v-if="clicked" :class="clicked ? 'darkAni': ''"></div>
    </div>
    <div v-if="isCooking || !isCooking && checkIfCaught">
      <div v-if="situNum === 1">
        <img src="../assets/media/goldenEgg.svg" class="egg" v-hammer:swipe.down="eggTo" :class="eggToBowl ? 'downAni': ''" @animationend="situNum++"/>
        <img src="../assets/media/bowl.png" class="bowlEnd"/>
      </div>
      <div v-if="situNum === 2">
        <img src="../assets/media/bowl.png" class="bowlStart" v-hammer:swipe.down="bowlTo" :class="bowlToPan ? 'downAni': ''" @animationend="situNum++"/>
        <img src="../assets/media/panNoEgg.png" class="panNoEggEnd"/>
      </div>
      <div v-if="situNum === 3">
        <img src="../assets/media/panWithEgg.png" class="panNoEggStart" v-hammer:swipe.down="cookedTo" :class="cookedToPlate ? 'downAni': ''" @animationend="situNum++"/>
        <img src="../assets/media/plateNoEgg.png" class="plateNoEgg"/>
      </div>
      <div v-if="situNum === 4"> 
        <img src="../assets/media/plate.png" class="plateAni plateEgg" @animationend="showText = true"/>
        <div class="text" v-if="showText">בתיאבון!</div>
      </div>
      <div class="white-screen"></div>
    </div>
  </div>
</template>
 
<script>

export default {
  name: "kitchen",
  props: ["isCaught"],
  components: {

  },
  data() {
    return {
      clicked: false,
      isCooking: false,
      eggToBowl: false,
      bowlToPan: false,
      cookedToPlate: false,
      situNum: 1,
      showText: false
    }
  },
  methods: {
    nextScreen() {
      this.clicked = true; 
      setTimeout(() => {
        this.isCooking = true;
        this.$emit("next-page");
      }, 2300);
    },
    eggTo() {
      this.eggToBowl = true;
    },
    bowlTo() {
      this.bowlToPan = true;
    },
    cookedTo() {
      this.cookedToPlate = true;
    }
  },
  computed: {
    checkIfCaught() {
      if (this.isCaught) {
        return(true);
      } else {
        return(false);
      }
    }
  }
}
</script>

<style scoped> 
@font-face {
  font-family: "rubik";
  src: url("../assets/font/Rubik-Regular.ttf");
}

@font-face {
  font-family: "rubik-black";
  src: url("../assets/font/Rubik-Black.ttf");
}

html,
body {
  margin: 0;
  overflow: hidden;
}

.text {
  font-family: "rubik-black";
  color: rgb(1, 16, 95);
  font-size: 14vw;
  position: absolute;
  top: 14vh;
  left: 50%;
  transform: translateX(-50%);
  z-index: 5;
  direction: rtl;
}

#kitchen {
  background-image: url("../assets/media/kitchen.jpg");
  width: 100vw;
  height: 100vh;
  background-size: 100% 100%;
}

.bitso {
  width: 40vw;
  position: absolute;
  height: 50vh;
  top: 60vh;
  right: 5vw;
}

.jail {
  width: 30vw;
  position: absolute;
  height: 15vh;
  top: 75vh;
  left: 40vw;
}

.speech-bub {
  width: 80vw;
  height: 40vh;
  position: absolute;
  top: 25vh;
  left: 50%;
  transform: translateX(-50%);
}

.main-txt {
  color: rgb(1, 16, 95);
  font-family: "rubik";
  font-size: 7vw;
  width: 70vw;
  text-align: center;
  direction: rtl;
  position: absolute;
  top: 35vh;
  left: 50%;
  transform: translateX(-50%);
}

.yes-btn {
  background-color: rgb(1, 16, 95);
  border-radius: 20px;
  border-style: none;
  color: white;
  font-size: 7vw;
  padding: 0.5vh 3vw;
  position: absolute;
  top: 47vh;
  left: 50%;
  transform: translateX(-50%);
}

.bowlEnd,
.bowlStart,
.plateNoEgg {
  position: absolute;
  width: 60vw;
  left: 50%;
  transform: translateX(-50%);
  height: auto;
  z-index: 5;
}

.bowlEnd {
  top: 50vh;
}

.bowlStart {
  top: 5vh;
}

.plateNoEgg {
  top: 60vh;
}

.panNoEggEnd,
.panNoEggStart {
  position: absolute;
  width: 90vw;
  left: 14%;
  transform: translateX(-50%);
  height: auto;
  z-index: 5;
  transform: rotate(-20deg);
}

.panNoEggEnd {
  top: 60vh;
}

.panNoEggStart {
  top: 10vh;
}

.black-screen,
.white-screen {
  width: 100vw;
  height: 100vh;
  position: absolute;
}

.white-screen {
  background-color: rgb(255, 255, 255, 0.6);
}

.black-screen {
  background-color: rgb(0, 0, 0, 0.9);
  z-index: 3;
}

.egg {
  position: absolute;
  top: 10vh;
  left: 50%;
  transform: translateX(-50%);
  width: 30vw;
  z-index: 5;
}

.plateEgg {
  position: absolute;
  top: 60vh;
  left: 50%;
  transform: translateX(-50%);
  z-index: 5;
  width: 60vw;
  height: auto;
}

.darkAni {
  animation: black 2.5s linear;
}

.jailAni {
  animation: jail 2.5s ease-out both;
}

.bitsoAni {
  animation: bitso 1.5s ease-out both;
}

.downAni {
  animation: down 1s ease-out both;
}

.plateAni {
  animation: plate 3s ease-out both;
}
@keyframes black {
  0% {
    opacity: 0.3;
  } 10% {
    opacity: 1;
  } 20% {
    opacity: 0.3;
  } 30% {
    opacity: 1;
  } 40% {
    opacity: 0.3;
  } 50% {
    opacity: 1;
  } 60% {
    opacity: 0.3;
  } 70% {
    opacity: 1;
  } 80% {
    opacity: 0.3;
  } 90% {
    opacity: 1;
  } 100% {
    opacity: 0.3;
  }
}

@keyframes jail {
  0% {
    z-index: 2;
  }
  100% {
    width: 50vw;
    height: 25vh;
    left: 80vw;
    top: 85vh;
    z-index: 2;
  }
}

@keyframes bitso {
  100% {
    transform: rotate(-100deg);
    width: 30vw;
    height: 35vh;
  }
}

@keyframes down {
  100% {
    top: 55vh;
    z-index: 6;
  }
}

@keyframes plate {
  100% {
    top: 30vh;
    width: 90vw;
  }
}
</style>