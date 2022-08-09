<template>
  <div id="black-screen">
    <div class="black">
      <div v-show="currPage === 1">
        <p class="line-1 line" :class="animationNum >= 0 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[0].line1 }}</p>
        <p class="line-2 line" :class="animationNum >= 1 ? 'anim-typewriter-short display': '' " @animationend="animationNum++" >{{ writeText[0].line2 }}</p>
        <div class="id" :class="animationNum >= 2 ? 'display': '' ">
          <img src="../assets/media/goldenEgg.svg" class="goldenEgg">
        </div>
        <p class="line-3 line" :class="animationNum >= 3 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[0].line3 }}</p>
        <p class="line-4 line" :class="animationNum > 5 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[0].line4 }}</p>
        <p class="line-5 line" :class="animationNum > 7 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[0].line5 }}</p>
        <p class="line-6 line" :class="animationNum > 8 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[0].line6 }}</p>
        <p class="line-7 line" :class="animationNum > 10 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[0].line7 }}</p>
        <p class="line-8 line" :class="animationNum > 12 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[0].line8 }}</p>
        <button class="blackBtn" :class="animationNum > 14 ? 'display': '' " @click="currPage++">אני בפנים</button>
      </div>
      <div v-show="currPage === 2">
        <p class="line-1 line" :class="animationNum >= 14 ? 'anim-typewriter-short display': '' " @animationend="animationNum++" >{{ writeText[1].line1 }}</p>
        <p class="line-2 line" :class="animationNum > 16 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[1].line2 }}</p>
        <p class="line-3-2 line" :class="animationNum > 18 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[1].line3 }}</p>
        <p class="line-4-2 line" :class="animationNum > 20 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[1].line4 }}</p>
        <div>
          <img src="../assets/media/sunGlasses.png" class="sunGlasses" :class="animationNum >= 25 ? 'display': '' ">
        </div>
        <p class="line-5-2 line" :class="animationNum > 22 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[1].line5 }}</p>
        <p class="line-6-2 line" :class="animationNum > 24 ? 'anim-typewriter display': '' " @animationend="animationNum++; $emit('next-page'); currPage++" >{{ writeText[1].line6 }}</p>
      </div>
      <div v-show="currPage === 3">
        <p class="line-1 line" :class="animationNum >= 26 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[2].line1 }}</p>
        <p class="line-2 line" :class="animationNum > 28 ? 'anim-typewriter display': '' " @animationend="animationNum++; $emit('next-page'); currPage++">{{ writeText[2].line2 }}</p> 
      </div>
      <div v-show="currPage === 4 && isCaught === true">
        <p class="line-1 line" :class="animationNum >= 28 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[3].line1 }}</p>
        <p class="line-2 line" :class="animationNum > 30 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[3].line2 }}</p>
        <p class="line-3-2 line" :class="animationNum > 32 ? 'anim-typewriter-short display': '' " @animationend="animationNum++" >{{ writeText[3].line3 }}</p>
        <div  :class="animationNum > 33 ? 'display': ''">
          <img src="../assets/media/jailBars.png" class="jailBars" v-if="animationNum > 33"/>
          <img src="../assets/media/goldenEgg.svg" class="bitso-jail" v-hammer:swipe.up="swipe" :class="swiped ? 'anim-jail': '' " @animationend="animationNum++" v-if="animationNum > 33"/>
        </div>
        <button class="blackBtn" :class="animationNum > 34 ? 'display': '' " @click="trysfds">להמשך הלמידה</button>
      </div>
      <div v-show="currPage === 4 && isCaught === false">
        <p class="line-1 line" :class="animationNum >= 28 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[4].line1 }}</p>
        <p class="line-2 line" :class="animationNum > 30 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[4].line2 }}</p>
        <p class="line-3-2 line" :class="animationNum > 32 ? 'anim-typewriter-short display': '' " @animationend="animationNum++" >{{ writeText[4].line3 }}</p>
        <img src="../assets/media/goldenEgg.svg" class="bitso-jail" v-if="animationNum > 33"/>
        <img src="../assets/media/eggInJail.png" class="jailBars" v-if="animationNum > 33"/>
        <button class="blackBtn" :class="animationNum > 34 ? 'display': '' " @click="currPage++">אוי לא! מה נעשה?</button>
      </div>
      <div v-show="currPage === 5 && isCaught === false">
        <p class="line-1 line" :class="animationNum >= 34 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[5].line1 }}</p>
        <p class="line-2 line" :class="animationNum > 36 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[5].line2 }}</p>
        <p class="line-3-2 line" :class="animationNum > 38 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[5].line3 }}</p>
        <div class="glowText line-4-2" @click="openLetter = true"  v-show="animationNum > 39">קרא את המכתב שביצו שלח לך</div>
        <div class="letter" v-if="openLetter">חשבת שתוכל לעצור אותי? אם אי פעם תרצה לראות את הביצים שלך בחזרה, תפגוש אותי במטבח של חדר אוכל C .מחר בשלוש עם 5 מיליון דולר במזומן</div>
        <button class="blackBtn" v-if="openLetter" @click="currPage++" :class="animationNum > 38 ? 'display': '' ">סיימתי לקרוא</button>
      </div>
       <div v-show="currPage === 6 && isCaught === false">
        <p class="line-1 line" :class="animationNum >= 38 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[6].line1 }}</p>
        <p class="line-2 line" :class="animationNum > 42 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[6].line2 }}</p>
        <p class="line-3-2 line" :class="animationNum > 44 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[6].line3 }}</p>
        <p class="line-4-2 line" :class="animationNum > 47 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[6].line4 }}</p>
        <p class="line-4-2 line" :class="animationNum > 49 ? 'anim-typewriter-short display': '' " @animationend="animationNum++" >{{ writeText[6].line5 }}</p>
        <button class="blackBtn" v-if="openLetter" @click="currPage++; $emit('next-page')" :class="animationNum > 49 ? 'display': '' ">להמשיך ללמידה</button>
      </div>
      <div v-show="currPage === 7 && isCaught === false">
        <p class="line-1 line" :class="animationNum >= 49 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[7].line1 }}</p>
        <p class="line-2 line" :class="animationNum > 50 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[7].line2 }}</p>
        <p class="line-2 line" :class="animationNum > 55 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[7].line3 }}</p>
        <button class="blackBtn" @click="currPage++; $emit('next-page')" :class="animationNum > 55 ? 'display': '' " v-if="animationNum > 40">אני רוצה להתחיל</button>
      </div>
      <div v-show="currPage === 8 && isCaught === false">
        <p class="line-1 line" :class="animationNum >= 55 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[8].line1 }}</p>
        <p class="line-2 line" :class="animationNum > 4 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[8].line2 }}</p>
        <p class="line-3-2 line" :class="animationNum > 4 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[8].line3 }}</p>
        <p class="line-4-2 line" :class="animationNum > 4 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[8].line4 }}</p>
        <img src="../assets/media/jailBars.png" class="jailBars" v-if="animationNum > 4"/>
        <img src="../assets/media/goldenEgg.svg" class="bitso-jail" v-hammer:swipe.up="swipe" :class="swiped ? 'anim-jail': '' " @animationend="currPage++; animationNum++" v-if="animationNum > 4"/>
      </div>
      <div v-show="currPage === 9 && isCaught === false">
        <p class="line-1 line" :class="animationNum >= 4 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[9].line1 }}</p>
        <p class="line-2 line" :class="animationNum > 4 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[9].line2 }}</p>
        <button class="blackBtn" @click="currPage++; $emit('next-page')" :class="animationNum > 4 ? 'display': '' ">אני רוצה להכין חביתה</button>
      </div>
      <div v-show="currPage === 5 && isCaught === true">
        <p class="line-1 line" :class="animationNum >= 36 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[9].line1 }}</p>
        <p class="line-2 line" :class="animationNum > 38 ? 'anim-typewriter display': '' " @animationend="animationNum++" >{{ writeText[9].line2 }}</p>
        <button class="blackBtn" @click="$emit('next-page')" :class="animationNum > 39 ? 'display': '' ">אני רוצה להכין חביתה</button>
      </div>
    </div>
  </div>
</template>
 
<script>

export default {
  name: "black-screen",
  props: ["isCaught"],
  data() {
    return {
      currPage: 1,
      animationNum: 0,
      lineNum: 1,
      swiped: false,
      timer: "",
      openLetter: false,
      writeText: [{
        "line1": "המטרה: לחטוף את הביצה הזהובה.",
        "line2": "המידע:",
        "line3": "יש בידינו מידע שביצו עובר ",
        "line4": "מלול אל לול וסוחר בביצים. הוא",
        "line5": "כל כך טוב בלהתחזות כך שעד כה",
        "line6": "איש עוד לא תפס אותו. ",
        "line7": "אתה חייב לעצור אותו לפני שגם ",
        "line8": "הבסיס שלנו יפגע. ",
      },
      {
        "line1": "כמו שחשבנו. ",
        "line2": "נעביר לך עוד פרטים בהמשך.",
        "line3": "תשמור על עצמך - ואל תיתפס. ",
        "line4": "תוכל לראות את כל הפרטים ועזרה ",
        "line5": "נוספת בעזרת משקפי המרגלים. ",
        "line6": "בהצלחה. "
      },
      {
        "line1": "המשקפיים יגלו לך את ביצו. ",
        "line2": "השתמש בהן בחוכמה. "
      },
      {
        "line1": "כל הכבוד, ידענו שאפשר לסמוך",
        "line2": "עליך. ניתן לך את הכבוד לשים את ",
        "line3": "ביצו בכלא. "
      },
      {
        "line1": "נכשלת במשימה. ביצו הצליח לחטוף ",
        "line2": "את הביצים שאספת ועכשיו הוא ברח ",
        "line3": "לסחור בהן בהודו. "
      },
      {
        "line1": "אל תדאג. זאת לא ההזדמנות ",
        "line2": "האחרונה שלך להציל את הביצים", 
        "line3": "ולהכניס את ביצו לכלא. "
      },
      {
        "line1": "יש לנו רעיון מאיפה תוכל להשיג ",
        "line2": "את הכסף. רשמנו אותך לחידון ",
        "line3": "הביצים הבינלאומי שמתקיים מחר ",
        "line4": "בשלוש. אבל אתה חייב להמשיך ",
        "line5": "להתכונן אליו. "
      },
      {
        "line1": "עכשיו כשסיימת ללמוד, אתה מוכן ",
        "line2": "לחידון. תזכור – אסור לך להפסיד ",
        "line3": "כדי שתוכל להציל את הביצים. "
      },
      {
        "line1": "וואו, זה היה מרשים. ידענו ",
        "line2": "שאפשר לסמוך עליך שתציל את ",
        "line3": "הביצים ותתפוס את ביצו. ניתן ",
        "line4": "לך את הכבוד להכניס אותו לכלא. "
      },
      {
        "line1": "עכשיו כשסיימת ללמוד וביצו כבר ",
        "line2": "בכלא, נותר רק דבר אחד... "
      }]
    }
    
  },
  methods: {
    swipe() {
      this.swiped = true;
    },
    trysfds() {
      this.currPage++;
      this.$emit('next-page');
    }
  },
  computed: {
    
  }
}
</script>

<style scoped>
@font-face {
  font-family: "cour";
  src: url("../assets/font/cour.ttf");
}

@font-face {
  font-family: "rubik";
  src: url("../assets/font/Rubik-Regular.ttf");
}

html,
body {
  margin: 0;
}

.black {
  font-family: "cour";
  background-color: black;
  background-size: 100% 100%;
  width: 100vw;
  height: 100vh;
  position: absolute;
  margin: 0;
  color: rgba(255,255,255,.75);  
  direction: rtl;
}

html{
  min-height: 100%;
  overflow: hidden;
}

.id {
  background-image: url("../assets/media/ID.png");
  position: absolute;
  width: 90vw;
  height: 35vh;
  background-size: 100% 100%;
  top: 15vh;
  right: 5vw;
  display: none;
}

.goldenEgg {
  width: 35%;
  height: 70%;
  position: absolute;
  right: 60%;
  top: 10%;
}

.sunGlasses {
  display: none;
  width: 90vw;
  height: 50vh;
  position: absolute;
  top: 15vh;
  left: 50%;
  transform: translateX(-50%);
}

.line {
  display: none;
  font-size: 5vw;
  direction: rtl;
  position: relative;
  top: 10%;  
  margin: 0 5vw;
  border-left: 10px solid transparent;
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  transform: translateY(-50%);    
}

.blackBtn {
  background-color: transparent;
  border-style: solid;
  border-color: rgba(255,255,255,.75);
  color: rgba(255,255,255,.75);
  font-family: "cour";
  font-size: 5vw;
  padding: 2vw 4vh;
  position: absolute;
  top: 80vh;
  left: 50%;
  transform: translateX(-50%);
  display: none;
}

.letter {
  background-color: white;
  color: black;
  font-family: "rubik";
  width: 70vw;
  padding: 2vh 4vw;
  direction: rtl;
  font-size: 7vw;
  position:absolute;
  top: 30vh;
  left: 50%;
  transform: translateX(-50%);
}

.line-1 {
  top: 8vh;
}

.line-2 {
  top: 8.5vh;
}

.line-3 {
  top: 50vh;
}

.line-4 {
  top: 50.5vh;
}

.line-5 {
  top: 51vh;
}

.line-6 {
  top: 51.5vh;
}

.line-7 {
  top: 52vh;
}

.line-8 {
  top: 52.5vh;
}

.line-3-2 {
  top: 9vh;
}

.line-4-2 {
  top: 9.5vh;
}

.line-5-2 {
  top: 10vh;
}

.line-6-2 {
  top: 40vh;
}

.jailBars {
  width: 60vw;
  height: 20vh;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  top: 22vh;
  z-index: 4;
}

.bitso-jail {
  width: 25vw;
  height: auto;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  top: 60vh;
  z-index: 3;
}
/* Animation */
.anim-typewriter {
  animation: typewriter 3.2s steps(44) normal both,
  blinkTextCursor 500ms steps(44) 7 both;
}

.anim-typewriter-short {
  animation: typewriterShort 1.5s steps(20) normal both,
  blinkTextCursor 500ms steps(20) 2 both;
}

.anim-jail {
  animation: jail 2s ease-out both;
}

.display {
  display: block;
}

.glowText {
  text-align: center;
  top: 19vh;
  left: 50%;
  transform: translateX(-50%);
  position: absolute;
  text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 30px rgb(250, 250, 250), 0 0 40px rgb(240, 240, 240), 0 0 50px rgb(250, 250, 250), 0 0 60px rgb(240, 240, 240);
  color: white;
}

@keyframes typewriter{
  from{width: 0;}
  to{width: 18em;}
}

@keyframes typewriterShort{
  from{width: 0;}
  to{width: 9em;}
}

@keyframes blinkTextCursor{
  from{border-left-color: rgba(255,255,255,.75);}
  to{border-left-color: transparent;}
}

@keyframes jail {
  from{top: 60vh;}
  to{top: 22vh;}
}
</style>