<template>
    <div id="home_page">
      <div class="top_symbols">
        <img src="../assets/symbols/PeleSymbol.svg" alt="PeleSymbol" id="pele_symbol" />
        <img src="../assets/symbols/BahalagSymbol.svg" alt="BahalgSymbol" id="bahalag_symbol" />
       <img src="../assets/symbols/HomeTitle.svg" alt="Titles" id="titles" />
     </div>
      <div id="button_container">
        <img src="../assets/symbols/chapters/trainingProgram.svg" alt="תוכנית הכשרה" id="program" class="subject" @click="switchScreen"/>
        <img src="../assets/symbols/chapters/trainingFaculty.svg" alt="סגל הכשרה" id="faculty" class="subject" @click="switchScreen"/>
        <img src="../assets/symbols/chapters/students.svg" alt="חניכים" id="students" class="subject" @click="switchScreen"/>
      </div>
    </div>
</template>


<script>

export default {
  name: "home-page",
  data() {
    return {
    }
  },
  methods: {
    switchScreen(event) {
      this.$emit("picked-subject", event.target.id);
      this.$emit("curr-page", 3);
    }
  }

}
</script>

<style scoped>
#home_page {
   background-image: url("../assets/photos/TalebBackground.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    height: 100%;
    width: 100%;
}

.top_symbols {
    position: absolute;
    width: 100vw;
    height: 10vh;
    top: 0svh;
}

#bahalag_symbol {
    position: absolute;
    height: 10vh;
    width: 20vw;
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
    height: 100%;
    width: 55%;
    left: 22%;
    top: 0%;
}

#button_container {
    position: absolute;
    width: 100vw;
    height: 70vh;
    top: 8vh;
}

/* subjects */

.subject {
  position: absolute;
  height: 26%;
  width: 30%;
    
}

#management {
  left: 32%;
  top: 2%;
  position: absolute;
  height: 28%;
  width: 35%;
}

#program {
  right: 36%;
  top: 32%;
}

#faculty {
  right: 17%;
  bottom: 10%;
}

#students {
     bottom: 10%;
     left: 15%;
}

#environment {
     top: 32%;
     left: 4%;
}


</style>