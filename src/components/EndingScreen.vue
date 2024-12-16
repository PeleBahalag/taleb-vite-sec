<template>
  <div id="ending_screen">
    <h1 id="winning_text" class="changing_title" v-if="playerStat === 0">
      כל הכבוד! עברת את המבחן בהצלחה
    </h1>
    <h1 id="losing_text" class="changing_title" v-if="playerStat === 1">
        לצערנו לא עברת את המבחן 
    </h1>
    <p id="score"> {{this.scorePlayer}} ציונך הוא</p>
    <p id="explain">
      אם תרצו לחזור למסך הבית לחצו על הכפתור השמאלי בתחתית העמוד, אם תרצו להתחיל
      את התרגול מחדש לחצו על הכפתור הימני שבתחתית העמוד
    </p>
    <div id="button_containers">
      <img
        src="../assets/symbols/HomeSymbol.svg"
        alt="Home Button"
        id="home_button"
        @click="changePage"
      />
      <img
        src="../assets/gameSymbols/TryAgain.svg"
        alt="Return Buttom"
        id="return_button"
        @click="changePage"
      />
    </div>
  </div>
</template>


<script>
export default {
  name: "ending-screen",
  props: ["playerStat", "scorePlayer"],
  data() {
    return {
      winOrLose: this.playerStat,
    };
  },
  methods: {
    changePage(event) {
      if (event.target.id === "home_button") {
        this.$emit("curr-page", 2);
      } else if (event.target.id === "return_button") {
        this.$emit("curr-page", 4);
      }
    },
  },
};
</script>

<style scoped>
@font-face {
  font-family: MyFont;
  src: url("../assets/fonts/IBMPlexSansHebrew-Regular.ttf");
}

#ending_screen {
  background-image: url("../assets/photos/GameBackground.jpg");
  background-size: cover;
  background-repeat: no-repeat;

  left: 0vw;
  top: 0vh;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  position: fixed;
}

.changing_title {
  position: absolute;
  height: 10vh;
  width: 75vw;
  font-family: MyFont;
  font-size: 6vw;
  color: white;
  text-align: center;
  top: 15vh;
  left: 13vw;
}

#button_containers {
  position: absolute;
  height: 20vh;
  width: 85vw;
  bottom: 15vh;
  left: 10vw;
}

#home_button {
  position: absolute;
  height: 45%;
  width: 39%;
  left: 5%;
}

#return_button {
  position: absolute;
  height: 45%;
  width: 39%;
  right: 5%;
}

#explain {
  position: absolute;
  height: 25%;
  width: 85%;
  font-family: MyFont;
  font-size: 5vw;
  color: white;
  text-align: center;
  top: 40%;
  left: 8%;
}

#score {
  position: absolute;
  height: 10%;
  width: 85%;
  font-family: MyFont;
  font-size: 4.5vw;
  color: white;
  text-align: center;
  top: 30%;
  left: 7%;
}
</style>