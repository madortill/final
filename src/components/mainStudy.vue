<template>
  <div id="main">
    <img class="eggDecor" src="../assets/media/egg.svg"/>
    <img class="eggDecorNest" src="../assets/media/chickenNest.png"/>
    <div class="textArea">
      <div class="header">{{ headerArr[currLaw] }}</div>
      <div class="mainText">{{ textArr[currLaw] }}</div>
    </div>
    <img class="next" src="../assets/media/arrow.png" @click="nextRule"/>
  </div>
</template>
 
<script>
export default {
  name: "main-study",
  components: {
  },
  data() {
    return {
      textArr: [
        "אז, כמו שאמרנו – נלמד היום כמה עקרונות בסיסיים באסיפת ביצים.",
        "הביצה צריכה להיאסף בין שלושים דקות לשעה אחרי שהוטלה. לא יותר ולא פחות.",
        "בעיר הבהדים אוספים ביצים שהוטלו רק מתרנגולות בצבע אדום.",
        "למדת את כל החוקים שצריך לדעת כדי לאסוף ביצים. רוצה לחזור על מה שלמדת?"
      ],
      headerArr: [
        "בואו נתחיל!",
        "חוק ראשון",
        "חוק שני",
        "כל הכבוד!"
      ],
      currLaw: 0
    }
  },
  methods: {
    nextRule() {
      this.currLaw++;
      if(this.currLaw === 2 || this.currLaw === 3 || this.currLaw === 4) {
        this.$emit("next-page");
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

html,
body {
  margin: 0;
  overflow: hidden;
}

#main {
  background-color: rgb(255, 255, 204);
  width: 100vw;
  height: 100vh;
}

.eggDecorNest {
  position: absolute;
  top: 6vh;
  height: auto;
  width: 100vw;
  left: 50%;
  transform: translateX(-50%);
}

.eggDecor {
  position: absolute;
  top: 2vh;
  width: 50vw;
  left: 50%;
  transform: translateX(-50%);
}

.textArea {
  background-color: rgb(255, 255, 255, 0.7);
  width: 80vw;
  height: 35vh;
  border-radius: 40px;
  position: absolute;
  top: 49vh;
  left: 50%;
  transform: translateX(-50%);
}

.header,
.mainText {
  font-family: "rubik";
  color: rgb(1, 16, 95);
  font-weight: bold;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  direction: rtl;
}

.header {
  font-size: 8.5vmin;
  top: 12%;
}

.back,
.next {
  width: 10vw;
  height: 5vh;
  position: absolute;
}

.back {
  top: 2vh;
  right: 4vw;
}

.next {
  top: 93vh;
  left: 4vw;
}

.mainText {
  font-size: 6vmin;
  text-align: center;
  direction: rtl;
  width: 60vw;
  top: 60%;
  transform: translate(-50%, -50%);
}
</style>