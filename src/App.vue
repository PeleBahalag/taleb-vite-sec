<template>
  <div id="app">
    <starter-comp v-if="showPage === 1" @curr-page="switchScreen"></starter-comp>
    <home-page v-if="showPage === 2" @curr-page="switchScreen" @picked-subject="subjectSwitch"></home-page>
    <study-page v-if="showPage === 3" @curr-page="switchScreen" :subjectsName="pickedName" :subNumber="pickedNumber"></study-page>
    <game-home  v-if="showPage === 4" @curr-page="switchScreen" @player-status="playerState" :subNumber="pickedNumber"></game-home>
    <ending-screen v-if="showPage === 5" @curr-page="switchScreen" :playerStat="winOrLose"  :scorePlayer="score"></ending-screen>
  </div>
</template>

<script>
import HomePage from "./components/HomePage.vue";
import StudyPage from "./components/StudyPage.vue";
import GameHome from "./components/GameHome.vue";
import EndingScreen from "./components/EndingScreen.vue";
import StarterComp from './components/StarterComp.vue';

export default {
  name: "app",
  data() {
    return {
      showPage: 1,
      pickedName: "",
      pickedNumber: 0,
      winOrLose: 0,
      score: 0,
    }
  },
  components: {
    HomePage,
    StudyPage,
    GameHome,
    EndingScreen,
    StarterComp,
  },
  methods: {
    switchScreen(pageNum) {
      this.showPage = pageNum;
    },
    subjectSwitch(subName){
      this.pickedName = subName;
      console.log(this.pickedName);
    switch(this.pickedName) {
      case "program":
        this.pickedNumber = 0;
      break;
      case "faculty":
        this.pickedNumber = 1;
      break;
      case "students":
        this.pickedNumber = 2;
      break;
    default:
    // code block
}
    },


    playerState(player, score){
      console.log(score);
      this.score = score;
      this.winOrLose = player;
    }
  }

}
</script>

<style>
* {
  height: 100vh;
  width: 100vw;
    overflow: hidden;
  position: fixed;
    right: 0vw;
  bottom: 0vh;
}

/* #app{
    height: 100vh;
  width: 100vw;
} */


</style>
