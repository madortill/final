<template>
  <div id="quiz">
  <div class="bg">
    <img src="../assets/media/eggCrown.svg" class="egg-crown"/>
    <div v-if="part === 0 || part === 4">
      <div class="header">{{ textArr[part].header }}</div>
      <div class="mainText1">
        <div class="line">{{ textArr[part].line }}</div>
      </div>
      <img class="next" src="../assets/media/backWhite.svg" @click="part === 4 ? $emit('next-page'): part++; isCorrect = ''; chose = ''" v-if="isCorrect === ''"/>
    </div>
    <div v-if="part >= 1 && part < 4">
      <div class="header1">{{ textArr[part].header }}</div>
        <div class="mainText">
        <div class="question">{{ textArr[part].question }}</div>
        <div class="buttons" :class="isCorrect ? 'disable': ''">
          <div v-for="n in 4" :key="n" class="answer" :id="'answer' + n" @click="chose = n" :class="chose === n ? 'chosen': ''"></div>
        </div>
        <div class="answers">
          <label for="answer1">{{ textArr[part].answer1 }}</label>
          <label for="answer2">{{ textArr[part].answer2 }}</label>
          <label for="answer3">{{ textArr[part].answer3 }}</label>
          <label for="answer4">{{ textArr[part].answer4 }}</label>
        </div>
      </div>
      <img class="next" src="../assets/media/backWhite.svg" @click="part++; isCorrect = ''; chose = '';" v-if="isCorrect"/>
    </div>
    <button class="check-btn" v-if="chose !== '' && !isCorrect" @click="checkAnswer">בדיקה</button>
  </div>
  </div>
</template>
 
<script>

export default {
  name: "quiz",
  components: {

  },
  data() {
    return {
      textArr: [{
        "header": "ברוכים הבאים לחידון הביצים הגדול!",
        "line": "כאן תבחנו על חוקי הביצים, ותוכלו לזכות בפרס הגדול של 5 מיליון דולר במזומן!"
      },
      {
        "header": "חידה ראשונה",
        "line": "",
        "question": "מהו הצבע של ביצת תרנגולת?",
        "answer1": "כחול",
        "answer2": "סגול",
        "answer3": "ירוק",
        "answer4": "לבן ביצה",
        "correct": 4
      },
      {
        "header": "חידה שניה",
        "line": "",
        "question": "מהו טווח הזמנים בו מותר לאסוף ביצים?",
        "answer1": "בין חצי שעה לשעה",
        "answer2": "אחרי שלוש שעות",
        "answer3": "בין עשרים דקות לשעה",
        "answer4": "מתי שרוצים",
        "correct": 1
      },
      {
        "header": "חידה שלישית",
        "line": "",
        "question": "באיזה צבע התרנגולות שאוספים את ביציהן בעיר הבהדים?",
        "answer1": "כתום",
        "answer2": "סגול",
        "answer3": "אדום",
        "answer4": "כחול",
        "correct": 3
      },
      {
        "header": "",
        "line": "כל הכבוד! זכית בפרס הגדול והרווחת 5 מיליון דולר!"
      }],
      part: 0,
      chose: "",
      isCorrect: ""
    }
    
  },
  methods: {
    checkAnswer() {
      if(this.textArr[this.part].correct === this.chose) {
        this.isCorrect = true;
        document.getElementById(`answer${this.chose}`).classList.remove("chosen");
        document.getElementById(`answer${this.chose}`).classList.add("green");
      } else {
        this.isCorrect = false;
        document.getElementById(`answer${this.chose}`).classList.remove("chosen");
        document.getElementById(`answer${this.chose}`).classList.add("red");
      }
    }
  },
  computed: {
  }
}
</script>

<style scoped> 
@font-face {
  font-family: "rubik-black";
  src: url("../assets/font/Rubik-Black.ttf");
}

@font-face {
  font-family: "rubik";
  src: url("../assets/font/Rubik-Regular.ttf");
}

#quiz {
  background-image: url("../assets/media/gameShow2.jpg");
  width: 100vw;
  height: 100vh;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  direction: rtl;
}

.bg {
  width: 100%;
  height: 100%;
  background-color: rgb(0, 0, 0, 0.7);
}
.mainText,
.mainText1 {
  background-color: rgb(255, 255, 255, 0.7);
  width: 80vw;
  border-radius: 50px;
  position: absolute;
  left: 10vw;
}

.mainText1 {
  height: 30vh;
  top: 45vh;
}

.mainText {
  height: 50vh;
  top: 32vh;
}
.egg-crown {
  top: 0vh;
  width: 20vw;
  height: auto;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
}

.header,
.header1 {
  color: white;
  font-family: "rubik-black";
  text-align: center;
  position: absolute;
  width: 90vw;
  left: 50%;
  transform: translateX(-50%);
  font-weight: bold;
}

.header1 {
  font-size: 15vw;
  top: 18vh;  
}

.header {
  font-size: 11vw;
  top: 16vh;
}

.next {
  top: 90vh;
  left: 4vw;
  width: 9vw;
  height: 6vh;
  position: absolute;
  z-index: 6;
}

.line {
  font-family: "rubik";
  color: black;
  font-size: 7vw;
  font-weight: bold;
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 60vw;
}

.answers {
  display: flex;
  font-family: "rubik";
  color: black;
  font-size: 6vw;
  font-weight: bold;
  width: 60vw;
  height: 25vh;
  justify-content: space-between;
  flex-direction: column;
  flex-wrap: wrap;
  position: absolute;
  top: 40%;
  right: 25%;
}

.buttons {
  display: flex;
  width: 40vw;
  height: 25vh;
  justify-content: space-between;
  flex-direction: column;
  position: absolute;
  top: 40%;
  right: 10%;
}

.question {
  font-family: "rubik";
  color: black;
  font-size: 7vw;
  font-weight: bold;
  text-align: center;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 70vw;
  top: 7%;
}

.answer {
  background-color: white;
  border-radius: 50vw;
  border-style: solid;
  border-color: black;
  width: 6vw;
  height: 6vw;
}

.chosen {
  background-color: grey;
}

.white {
  background-color: white;
}

.green {
  background-color: green;
}

.red {
  background-color: red;
}

.check-btn {
  background-color: grey;
  border-style: solid;
  border-color: grey;
  border-radius: 20px;
  font-family: "rubik";
  color: black;
  font-size: 7vw;
  padding: 2vw 2vh;
  left: 50%;
  transform: translateX(-50%);
  position: absolute;
  top: 86vh;
  font-weight: bold;
}

.disable {
  pointer-events: none;
}
</style>