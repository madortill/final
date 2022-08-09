<template>
  <div id="app">
    <instructions v-show="sectionNum === 1 || sectionNum === 4 || sectionNum === 9" @next-page="nextPage"></instructions>
    <black-screen v-show="sectionNum === 2 || sectionNum === 5 || sectionNum === 7 || sectionNum === 11 && !isCaught || sectionNum === 13 && isCaught || sectionNum === 14 && !isCaught" @next-page="nextPage" :isCaught="isCaught"></black-screen>
    <main-study v-show="sectionNum === 3 || sectionNum === 8 || sectionNum === 11 && isCaught" @next-page="nextPage"></main-study>
    <first-game v-show="sectionNum === 6" @next-page="nextPage" @caught="isCaught = true"></first-game>
    <second-game v-show="sectionNum === 10" @next-page="nextPage"></second-game>
    <quiz v-show="sectionNum === 12" @next-page="nextPage"></quiz>
    <kitchen v-show="sectionNum === 13 && !isCaught || sectionNum === 14 && isCaught || sectionNum === 15 && !isCaught" @next-page="nextPage" :isCaught="isCaught"></kitchen>
  </div>
</template>
 
<script>
import blackScreen from '@/components/blackScreen.vue'
import firstGame from '@/components/firstGame.vue'
import mainStudy from '@/components/mainStudy.vue'
import instructions from '@/components/instructions.vue'
import secondGame from '@/components/secondGame.vue'
import quiz from '@/components/quiz.vue'
import kitchen from '@/components/kitchen.vue'

export default {
  components: {
    blackScreen,
    firstGame,
    mainStudy,
    instructions,
    secondGame,
    quiz,
    kitchen
  },
  data() {
    return {
      blackscreen: false,
      sectionNum: 1,
      isCaught: false
    }
  },
  methods: {
    nextPage() {
      this.sectionNum++;
    },
  }
}
</script>

<style scoped> 
html,
body {
  margin: 0;
}
</style>