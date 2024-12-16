<template>
  <div id="starter">
    <div class="top_symbols">
      <img
        src="../assets/symbols/BahalagSymbol.svg"
        alt="BahalgSymbol"
        id="bahalag_symbol"
      />
      <img
        src="../assets/symbols/PeleSymbol.svg"
        alt="PeleSymbol"
        id="pele_symbol"
      />
      <img
        src="../assets/symbols/ExplantionTitle.svg"
        alt="Titles"
        id="titles"
        v-if="titleImg === 1"
      />
      <img
        src="../assets/symbols/InstructionsTitle.svg"
        alt="Titles"
        id="titles"
        v-if="titleImg === 2"
      />
    </div>
    <div id="middle_part">
      <div id="first_part">
        <img
          src="../assets/symbols/LightSymbol.svg"
          alt="lightIcon"
          id="lightIcon"
        />
        <h1 id="head">ברוכים הבאים</h1>
        <h5 id="underline">ללומדת תל”ב של בית הספר להגנת הגבולות</h5>
        <img
          src="../assets/symbols/BooksSymbol.svg"
          alt="books"
          id="booksIcon"
        />
      </div>
      <p id="mainText"></p>
      <img
        src="../assets/photos/instructionOne.png"
        alt="instruction"
        id="instructions_img"
      />
    </div>
    <div id="bottom_part">
      <p id="little_text">!לחצו כדי להמשיך</p>
      <div id="on_click" @click="startPage"></div>
      <div id="last_click" @click="startPage"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "starter-comp",
  data() {
    return {
      nextPage: 0,
      titleImg: 1,
    };
  },
  methods: {
    startPage() {
      this.nextPage = this.nextPage + 1;

      if (this.nextPage === 1) {
        document.getElementById("first_part").innerHTML = "";
        document.getElementById("titles").style.visibility = "visible";
        document.getElementById(
          "mainText"
        ).innerText = `תל"ב = תקן לאיכות בהדרכה

         התל"ב מחולק לחמישה נושאים עיקריים לפי מימדי ההדרכה: ניהול הדרכה, תכנית הכשרה, סגל, חניכים, סביבה

         תל"ב, נועד ליצור סטנדרט באיכות ההדרכה במסגרות השונות

         כל כשנתיים מתקיימת ביקורת מטכ"לית
         
        נהלי תו התקן מהווים פקודה מחייבת לכלל ההכשרות בצה"ל`;
      } else if (this.nextPage === 2) {
        this.titleImg = this.titleImg + 1;
        document.getElementById("mainText").style.visibility = "hidden";
        document.getElementById("instructions_img").style.visibility =
          "visible";
        document.getElementById("last_click").style.visibility = "visible";
        document.getElementById("on_click").style.visibility = "hidden";
      } else if (this.nextPage === 3) {
        this.$emit("curr-page", 2);
      }
    },
  },
};
</script>

<style scoped>
#starter {
  background-image: url("../assets/photos/TalebBackground.jpg");
  /* background-color: pink; */
  background-size: cover;
  background-repeat: no-repeat;
  /* height: 100dvh;
  width: 100dvw; */
}

@font-face {
  font-family: MyFont;
  src: url("../assets/fonts/IBMPlexSansHebrew-Regular.ttf");
}

.top_symbols {
  position: absolute;
  width: 100vw;
  height: 10vh;
  top: 0vh;
}

#bahalag_symbol {
  position: absolute;
  height: 85%;
  width: 20%;
  left: 1%;
  top: 10%;
}

#pele_symbol {
  position: absolute;
  height: 85%;
  width: 20%;
  right: 1%;
  top: 15%;
}

#titles {
  position: absolute;
  height: 180%;
  width: 55%;
  left: 22%;
  top: -30%;
  visibility: hidden;
}

/* #middle_part {
  position: absolute;
  width: 95vw;
  height: 50vh;
  border: 2mm solid pink;
} */

#instructions_img {
  position: absolute;
  width: 89%;
  height: 70%;
  bottom: 19%;
  left: 5.5%;
  visibility: hidden;
}

#head {
  position: absolute;
  text-align: center;
  color: white;
  font-family: MyFont;
  position: absolute;
  width: 90%;
  height: 15%;
  top: 29%;
  left: 6%;
  font-weight: 3000vw;
  font-size: 13vw;
}

#underline {
  position: absolute;
  color: white;
  font-family: MyFont;
  position: absolute;
  text-align: center;
  width: 65%;
  height: 15%;
  top: 45%;
  left: 18%;
  font-weight: 1000vw;
  font-size: 6vw;
}

#lightIcon {
  position: absolute;
  width: 25%;
  height: 22%;
  left: 3%;
  top: 9%;
  transform: rotate(-22deg);
}

#booksIcon {
  position: absolute;
  width: 25%;
  height: 22%;
  right: 3%;
  top: 58%;
  transform: rotate(22deg);
}

#bottom_part {
  position: absolute;
  width: 95vw;
left: 1vw;
  height: 20vh;
  bottom: 0%;
}

#on_click {
  position: absolute;
  background-image: url("../assets/symbols/DownSymbol.svg");
  background-repeat: no-repeat;
  background-size: contain;
  width: 10%;
  height: 35%;
  left: 45%;
  top: 15%;
  cursor: pointer;
  visibility: visible;
}

#last_click {
  position: absolute;
  background-image: url("../assets/symbols/HomeSymbol.svg");
  background-repeat: no-repeat;
  background-size: contain;
  width: 10%;
  height: 35%;
  left: 45%;
  top: 15%;
  cursor: pointer;
  visibility: hidden;
}

#little_text {
  position: absolute;
  width: 45%;
  height: 30%;
  left: 30%;
  bottom: 60%;
  color: white;
  font-family: MyFont;
  font-weight: 1000vw;
}

#mainText {
  position: absolute;
  width: 95vw;
  height: 60vh;
  text-align: center;
  visibility: visible;
  top: 18vh;
  right: 1vw;
  color: white;
  font-family: MyFont;
  font-weight: 10vw;
  font-size: 4.5vw;
}


</style>