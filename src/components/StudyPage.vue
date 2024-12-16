<template>
    <div id="study_page">
      <div class="top_symbols">
        <img src="../assets/symbols/BahalagSymbol.svg" alt="BahalgSymbol" id="bahalag_symbol" />
        <img src="../assets/symbols/PeleSymbol.svg" alt="PeleSymbol" id="pele_symbol" />
       <img :src="img" alt="Titles" id="titles" />
     </div>
     <main-text v-if="showPlaces === 1" id="main_text" :subjectsName="subSaver" :subNumber="i" :innerPart="innerSub" :nameTitle="nameTitle" @make-progress="nextChapter" @made-progress="lastChapter"></main-text>
     <div id="text_container" v-if="showPlaces === 0">
        <div id="sub_text_list" v-for="(j, index) in optionArray[i]" :key="index" @click="updateSelected(index)" class="list-group-item">{{optionArray[i][index]}}</div>
     </div>
      <div id="bottom_part">
        <div id="home_click"  @click="startPage"></div>
        <div id="practice_click" @click="startPage" v-if="showPlaces === 0"></div>
     </div>
    </div>
</template>


<script>
import MainText from "./MainText.vue"



export default {
      name: "study-page",
      props: ['subjectsName', 'subNumber'],
  data() {
    return {
        subSaver: this.subjectsName,
        optionArray: [
            ['נוהל 2.3- הערכת חניכים (מבחנים בהכשרות)',
            'נוהל 2.4- תיק מדריך',
            ],
            ['נוהל 3.1- הגדרות תפקידם לסגלי הדרכה',
            'נוהל 3.3- הכנות מפקדים',
            'נוהל 3.4- פיתוח והערכת מפקדים',
            ],
            ['נוהל 4.1- נוהל טיפול בחניך מתקשה',
            'נוהל 4.3- בחירת חניך מצטיין וחניך למופת',
            'נוהל 4.4- תיק אישי חניך',
            ],
        ],
        img: `/src/assets/symbols/subjects/${this.subjectsName}.svg`,
        i: this.subNumber,
        showPlaces: 0,
        innerSub: "",
        nameTitle: "",
        saver: ""
    }
  },
  components: {
    MainText
  },
  methods: {
    startPage(event){
        if( this.showPlaces === 1){
            this.showPlaces = 0;
        }else {
            if(event.target.id === "home_click"){
                this.$emit("curr-page", 2);
            }else if(event.target.id === "practice_click"){
                this.$emit("curr-page", 4);
            }
        }
    },

    updateSelected(selectedPart) {
        console.log(this.optionArray[this.i][selectedPart]);
        this.nameTitle = this.optionArray[this.i][selectedPart];
        this.saver = selectedPart;
        this.innerSub = selectedPart;
        this.showPlaces = 1;
        document.getElementById("text_container").style.visibility = "hidden";
    },

    nextChapter(count){
        this.nameTitle = this.optionArray[this.i][count + 1];
    },
    lastChapter(count){
        this.nameTitle = this.optionArray[this.i][count - 1];
    }

  }
}
</script>


<style >
#study_page {
    background-image: url("../assets/photos/TalebBackground.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    height: 100%;
    width: 100%;
}

#main_text {
    position: absolute;
    width: 85%;
    height: 75%;
    top: 11%;
    left: 10%;
}

#sub_text_list{
    height: 10%;
    width: 95%;
    margin-left: 3%;
      margin-top: 7%;
  background-color: rgb(27, 148, 148);
    border-radius: 25px;
    text-align: center;
     position: relative;
}

.list-group-item {
     direction: rtl;
  text-decoration: none;
    font-family: MyFont;
    font-weight: 1000vw;
    font-size: 4vw;
  color: white;
  cursor: pointer;
}

/* .items{
    position: relative;
     direction: rtl;
  text-decoration: none;
    font-family: MyFont;
    font-weight: 1000vw;
    font-size: 4vw;
  color: white;
  cursor: pointer;
  right: 10%;
  bottom: 0%;
} */


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


#text_container {
    position: absolute;
    width: 90%;
    height: 50%;
    top: 11%;
    left: 6%;
    background-image: url("../assets/symbols/TextBackground.svg");
    background-size: cover;
    background-repeat: no-repeat;
    visibility: visible;
}


#color_text {
    color: white;
    text-align: center;
    font-family: MyFont;
    font-weight: 1000vw;
    font-size: 6vw;
}


#bottom_part {
    position: absolute;
    width: 100dvw;
    height: 14dvh;
    top: 86dvh;   
}


#home_click {
    position: absolute;
    background-image: url("../assets/symbols/HomeSymbol.svg");
    background-repeat: no-repeat;
    background-size: contain;
    width: 10%;
    height: 45%;
    left: 44%;
    bottom: 50%;
    cursor: pointer;
}


#practice_click{
    position: absolute;
    background-image: url("../assets/symbols/GameButton.svg");
    background-repeat: no-repeat;
    background-size: contain;
    width: 37%;
    height: 60%;
    left: 7%;
    bottom: 40%;
    cursor: pointer;
}


#back_button {
    position: absolute;
    background-image: url("../assets/symbols/BackwardsButton.svg");
    background-size: contain;
    background-repeat: no-repeat;
    width: 15%;
    height: 10%;
    bottom: 0%;
    right: 2%;

}

#next_button {
    position: absolute;
    background-image: url("../assets/symbols/NextButton.svg");
    background-size: contain;
    background-repeat: no-repeat;
    width: 15%;
    height: 10%;
     bottom: 0%;
     left: 2%;
}

#titles{
    position: absolute;
    height: 100%;
    width: 30%;
    right: 34%;
}
</style>