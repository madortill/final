<template>
  <div id="instructions">
    <div v-show="odot">
      <div class="abouts">
        <img src="../assets/media/bahad.png" class="bahad"/>
        <img src="../assets/media/mador.png" class="mador"/>
      </div>
      <div class="main-header" id="aboutHeader">אודות</div>
      <div class="odot-text">
        <div class="odotMain">{{ odotTxt[0].line1 }}</div>
        <div class="odotMain">{{ odotTxt[0].line2 }}</div>
        <div class="odotMain">{{ odotTxt[0].line3 }}</div>
        <div class="odotMain">{{ odotTxt[0].line4 }}</div>
        <div class="odotMain">{{ odotTxt[0].line5 }}</div>
        <div class="odotMain">{{ odotTxt[0].line6 }}</div>
      </div>
      <img src="../assets/media/arrow1.png" class="back" @click="odot = false"/>
    </div>
    <div class="first-page" v-show="page < 2 && !odot">
      <button class="abouts-btn" @click="odot = true">i</button>
      <div class="main-header">פינת הליטוף</div>
      <div class="textArea1">
        <div class="instruct-text">{{ textArr[page] }}</div>
      </div>
      <button class="start-btn" @click="nextText">{{ buttonArr[page] }}</button>
    </div>
    <div class="instruct" v-show="page >= 2 && !odot">
      <div class="textArea2">
        <div class="intruct-header">הוראות</div>
        <div class="instruct-text2">{{ textArr[page] }}</div>
      </div>
      <button class="start-btn" v-hammer:tap="nextText">התחל</button>
    </div>
  </div>
</template>
 
<script>
export default {
  name: "instructions",
  data() {
    return {
      textArr: [
        "אחרי שכל כך חיכית, סוף סוף הגיע היום הזה בשבוע. עליך לאסוף את הביצים מהלול כדי שתהיה לשאר הבסיס ארוחת צהריים! מרגיש שזה קצת גדול עליך?",
        "אל תדאג, תמיד יש פעם ראשונה. פה תלמד את כל מה שיש לדעת על איסוף ביצים.",
        "אספו את הביצים בזמן! אחרי שהוטלה ביצה, חכו את הזמן המתאים לאסוף אותה, אבל שימו לב שאתם לא מאחרים, אחרת היא תיעלם!",
        "אספו את הביצים הנכונות! אספו רק את הביצים שהוטלו על ידי התרנגולות הנכונות לפי החוק שלמדתם.",
      ],
      buttonArr: [
        "אני מרגיש אבוד...",
        "אפשר להתחיל?"
      ],
      odotTxt: [{
        "line1": 'מומחה תוכן: סג"מ בוריס שמשון',
        "line2": 'פיתוח: טוראי הדר יחזקאל',
        "line3": 'גרפיקה: טוראי הדר יחזקאל',
        "line4": 'רת"ח מופ: סמ"ר אופק בצון',
        "line5": 'רמ"ד טי"ל: רס"ן מיגל לויתן',
        "line6": 'גרסה: מאי 2022',
      }],
      page: 0,
      odot: false
    } 
  },
  methods: {
    nextText() {
      this.page++
      if(this.page === 2 || this.page === 3 || this.page === 4) {
        this.$emit("next-page");
      }
    }
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

html,
body {
  margin: 0;
  direction: rtl;
}

#instructions {
  background-image: url("../assets/media/bg.png");
  width: 100vw;
  height: 100vh;
  background-size: 100% 100%;
}

.main-header {
  font-family: "rubik-black";
  color: white;
  font-size: 30vmin;
  text-align: center;
  position: absolute;
  top: 5vh;
  text-shadow: 5px 5px rgb(1, 16, 95, 0.5);
  left: 50%;
  transform: translateX(-50%);
}

#aboutHeader {
  top: 10vh;
}

.textArea1,
.textArea2,
.odot-text {
  background-color: rgb(255, 255, 255, 0.7);
  width: 80vw;
  height: 34vh;
  border-radius: 40px;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  direction: rtl;
  line-height: 4.3vh;
}

.textArea1 {
  top: 46vh;
}

.textArea2 {
  top: 20vh;
}

.odot-text {
  top: 40vh;
}

.instruct-text,
.instruct-text2 {
  color: rgb(1, 16, 95);
  font-size: 6vw;
  font-family: "rubik";
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 60vw;
  font-weight: bold;
}

.instruct-text2 {
  margin-top: 2vh;
}

.odotMain {
  color: rgb(1, 16, 95);
  font-size: 6vw;
  font-family: "rubik";
  font-weight: bold;
  top: 4vh;
  position: relative;
  right: 2vw;
}

.intruct-header {
  font-weight: bold;
  color: rgb(1, 16, 95);
  font-size: 9vw;
  font-family: "rubik";
  text-align: center;
  left: 50%;
  transform: translateX(-50%);
  margin-top: 2vh;
  margin-bottom: 2vh;
  position: absolute;
}

.start-btn {
  direction: rtl;
  background-color: rgb(255, 255, 204);
  border-radius: 15px;
  border-color: transparent;
  padding: 2vw 2vh;
  font-weight: bold;
  color: rgb(1, 16, 95);
  font-size: 6vw;
  font-family: "rubik";
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  top: 87vh;
}

.bahad,
.mador {
  position: absolute;
  top: 1vh;
  height: auto;
}

.bahad {
  width: 12vw;
  right: 2vw;
}

.mador {
  width: 18vw;
  left: 2vw;
}

.abouts-btn {
  background-color: transparent;
  border-color: rgb(1, 16, 95);
  color: rgb(1, 16, 95);
  border-radius: 50px;
  border-style: solid;
  font-size: 6vw;
  padding: 0.5vh 4vw;
  font-family: "rubik";
  position: absolute;
  top: 1vh;
  left: 2vw;
  font-weight: bold;
  border-width: 4px;
}

.back {
  top: 92vh;
  position: absolute;
  width: 10vw;
  height: 5vh;
  right: 5vw;
}
</style>