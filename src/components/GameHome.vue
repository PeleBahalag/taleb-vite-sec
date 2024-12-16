<template>
  <div id="game_home">
    <div id="question_container">
      <h2
        id="question"
        v-if="saveName === 0"
        :key="program[currentQuestion].question"
      >
        {{ program[currentQuestion].question }}
      </h2>
      <h2
        id="question"
        v-if="saveName === 1"
        :key="faculty[currentQuestion].question"
      >
        {{ faculty[currentQuestion].question }}
      </h2>
      <h2
        id="question"
        v-if="saveName === 2"
        :key="students[currentQuestion].question"
      >
        {{ students[currentQuestion].question }}
      </h2>
    </div>
    <div id="choices_container">
      <div id="choices_box" v-if="saveName === 0">
        <div
          id="choices"
          v-for="(answer, index) in program[currentQuestion].answers"
          :key="index"
          v-bind:data-index="index"
        >
          <p id="text_answer" @click="selectAnswer" v-if="saveName === 0">
            {{ answer }}
          </p>
        </div>
      </div>
      <div id="choices_box" v-if="saveName === 1">
        <div
          id="choices"
          v-for="(answer, index) in faculty[currentQuestion].answers"
          :key="index"
          v-bind:data-index="index"
        >
          <p id="text_answer" @click="selectAnswer">{{ answer }}</p>
        </div>
      </div>
      <div id="choices_box" v-if="saveName === 2">
        <div
          id="choices"
          v-for="(answer, index) in students[currentQuestion].answers"
          :key="index"
          v-bind:data-index="index"
        >
          <p id="text_answer" @click="selectAnswer">{{ answer }}</p>
        </div>
      </div>
    </div>
    <p id="check_button" @click="checkAnswer">בדיקה</p>
  </div>
</template>

<script>
export default {
  name: "game-home",
  props: ["subNumber"],
  data() {
    return {
      program: [
        {
          question: "מה צריך לעשות טרם מבחן הערכת חניך, עיוני ומעשי?",
          answers: [
            "בעיוני יש לפרסם לחניכים את הנושאים עליהם הם עתידים להיבחן. במעשי יש לפרסם את דף ההערכה.",
            "בעיוני יש לפרסם את התשובות למבחן. במעשי יש לפרסם את דף ההערכה",
            "בעיוני יש לפרסם לחניכים את הנושאים עליהם הם עתידים להיבחן. במעשי יש לפרסם את מזג האוויר",
          ],
          correct_answer:
            "בעיוני יש לפרסם לחניכים את הנושאים עליהם הם עתידים להיבחן. במעשי יש לפרסם את דף ההערכה.",
        },
        {
          question:
            "נכון או לא נכון: לכל מבחן עיוני ייבנה דף הערכה אשר יכלול את הקריטריונים להערכת הביצוע של הנבחן.",
          answers: ["נכון", "לא נכון, מדובר על מבחן מעשי ולא עיוני"],
          correct_answer: "לא נכון, מדובר על מבחן מעשי ולא עיוני",
        },
        {
          question: "למה נועד תיק מדריך?",
          answers: [
            "התיק נועד לאפשר למדריך לדעת את השמות של החניכים",
            "התיק נועד לאגד את כלל הנספחים הקשורים לשיעור: תמונות, תרשימים וציורים",
            "התיק נועד לאפשר הכנה מקצועית של המפקד או מדריך, להביא לאחידות מקצועית ולתרום לזיכרון הארגוני.",
            "התיק נועד לאפשר סדר וארגון למדריכים על מנת להקל על הסגל",
          ],
          correct_answer:
            "התיק נועד לאפשר הכנה מקצועית של המפקד או מדריך, להביא לאחידות מקצועית ולתרום לזיכרון הארגוני.",
        },
        {
          question: "מה צריך לעשות לאחר שחייל נכשל במועד א?",
          answers: [
            "לתת לחייל לעשות את מועד ב ישר לאחר מכן",
            "לתת לחייל לעשות שוב את אותו המבחן",
            "לתת לחייל זמן ללמוד ולגשת למועד ב",
            "לתת לחייל לעשות את מועד ב עם עזרה מהסגל",
          ],
          correct_answer: "לתת לחייל זמן ללמוד ולגשת למועד ב",
        },
      ],
      faculty: [
        {
          question: "מה הוא אינו חלק מהגדרת תפקיד המכ",
          answers: [
            'יישום תוכנית ההכשרה בהתאם לפק"ש ולדווח על חריגה מהתכנון',
            "טיפול בפרט",
            "איתור וטיפול חניכים מתקשים",
            "תהליך הקניית הכשירות לחניכים וביצוע בקרה ומעקב אחר השגת הכשירויות בהכשרה.",
          ],
          correct_answer:
            "תהליך הקניית הכשירות לחניכים וביצוע בקרה ומעקב אחר השגת הכשירויות בהכשרה.",
        },
        {
          question:
            '"הכנת סגל תבנה בחילוק לארבעה צירים", בחר בתשובה השייכת לארבעת הצירים.',
          answers: ["הציר הפיקודי", "הציר המעשי", "הציר העיוני", "הציר הרפואי"],
          correct_answer: "הציר הפיקודי",
        },
        {
          question: "מה הוא פיתוח והערכת מפקדים?",
          answers: [
            "תהליך לאבחון רפואי של מפקדים",
            "תהליך שיטתי ומובן, המאורגן מראש הנותן מענה לצורך הפיקוד",
            "תהליך שיטתי ומובן, המאורגן בתוכנית קבועה מראש. התהליך מתחיל מיום קליטתו ועד סיום תפקידו.",
            "מאגד את כל ציוני המפקדים בקמפוס הדיגיטלי",
          ],
          correct_answer:
            "תהליך שיטתי ומובן, המאורגן בתוכנית קבועה מראש. התהליך מתחיל מיום קליטתו ועד סיום תפקידו.",
        },
        {
          question: "מי הנושא באחריות הכוללת על תוכנית חניכה והערכה לאיש סגל?",
          answers: ['מ"מ', 'משה"ד', 'מ"פ', 'סמ"פ'],
          correct_answer: 'מ"פ',
        },
      ],
      students: [
        {
          question: "דרכי הפעולה לקידום חניך:",
          answers: [
            "הפסקות ארוכות יותר כדי לתת לחניך להתרענן יותר בין שיעור לשיעור",
            "שעות תיגבור, זמנים ללמידה עצמית, מועדי מבחנים חוזרים, התנסויות והצמדת חונך מקצועי.",
            'לשלוח אותו לשיחת נזיפה אצל המ"פ ובמידת הצורך אצל המג"ד',
            "לבקש מהחניך הכי טוב בכיתה להסביר לו את החומר",
          ],
          correct_answer:
            "שעות תיגבור, זמנים ללמידה עצמית, מועדי מבחנים חוזרים, התנסויות והצמדת חונך מקצועי.",
        },
        {
          question: '"תהליך בחירת חניך מצטיין וחניך למופת נועד..."',
          answers: [
            "להגביר את הרצון להשקיע בהכשרה ולתגמל חניכים שהשקיעו.",
            "לתגמל את החייל שהכי טוב בעיניי המפקד",
            "להגביר את הרצון להשקיע לאחר פקודה",
            "לתגמל חניכים שהשקיעו במשימה",
          ],
          correct_answer:
            "להגביר את הרצון להשקיע בהכשרה ולתגמל חניכים שהשקיעו.",
        },
        {
          question: "מה מהבאים הוא מרכיב להצטיינות מופת?",
          answers: [
            "כושר קרבי",
            "מצטיין בר אור",
            "סוציומטרי עמיתים גבוה",
            "ציון סופי מעל 80",
          ],
          correct_answer: "סוציומטרי עמיתים גבוה",
        },
        {
          question: " מה צריך להיות תכונותיו של חניך למופת?",
          answers: [
            "השקעה, יוזמה, עזרה לזולת, התמדה, למידה והשתפרות",
            "יוזמה, עזרה לזולת, חתירה למצוינות והתמדה",
            "השקעה, חווד מפקד בולט לחיוב, עצמאות, קבלת האחר",
            "סוציומטרי עמיתים גבוה מאוד, התמדה, ציון סופי מעל 80, למידה והשתפרות",
          ],
          correct_answer: "השקעה, יוזמה, עזרה לזולת, התמדה, למידה והשתפרות",
        },
      ],
      currentQuestion: 0,
      answered: 0,
      wrongAnswers: 0,
      correctAnswers: 0,
      saveName: this.subNumber,
    };
  },
  methods: {
    selectAnswer(event) {
      var MyAnswer = event.target.innerText;
      this.answered = this.answered + 1;
      console.log(this.answered);

      switch (this.saveName) {
        case 0:
          if (MyAnswer !== this.program[this.currentQuestion].correct_answer) {
            if (this.program[this.currentQuestion + 1] === undefined) {
              this.wrongAnswers = this.wrongAnswers + 1;
              document.getElementById("check_button").style.display = "block";
            } else {
              this.wrongAnswers = this.wrongAnswers + 1;
              this.currentQuestion = this.currentQuestion + 1;
            }
          } else {
            if (this.program[this.currentQuestion + 1] === undefined) {
              this.correctAnswers = this.correctAnswers + 1;
              document.getElementById("check_button").style.display = "block";
            } else {
              this.correctAnswers = this.correctAnswers + 1;
              this.currentQuestion = this.currentQuestion + 1;
            }
          }
          break;
        case 1:
          if (MyAnswer !== this.faculty[this.currentQuestion].correct_answer) {
            if (this.faculty[this.currentQuestion + 1] === undefined) {
              this.wrongAnswers = this.wrongAnswers + 1;
              document.getElementById("check_button").style.display = "block";
            } else {
              this.wrongAnswers = this.wrongAnswers + 1;
              this.currentQuestion = this.currentQuestion + 1;
            }
          } else {
            if (this.faculty[this.currentQuestion + 1] === undefined) {
              this.correctAnswers = this.correctAnswers + 1;
              document.getElementById("check_button").style.display = "block";
            } else {
              this.correctAnswers = this.correctAnswers + 1;
              this.currentQuestion = this.currentQuestion + 1;
            }
          }
          break;
        case 2:
          if (MyAnswer !== this.students[this.currentQuestion].correct_answer) {
            if (this.students[this.currentQuestion + 1] === undefined) {
              this.wrongAnswers = this.wrongAnswers + 1;
              document.getElementById("check_button").style.display = "block";
            } else {
              this.wrongAnswers = this.wrongAnswers + 1;
              this.currentQuestion = this.currentQuestion + 1;
            }
          } else {
            if (this.students[this.currentQuestion + 1] === undefined) {
              this.correctAnswers = this.correctAnswers + 1;
              document.getElementById("check_button").style.display = "block";
            } else {
              this.correctAnswers = this.correctAnswers + 1;
              this.currentQuestion = this.currentQuestion + 1;
            }
          }
          break;
        default:
      }
    },

    checkAnswer() {
      switch (this.correctAnswers) {
        case 0:
          console.log("my friend1");
          this.$emit("player-status", 1, 0);
          this.$emit("curr-page", 5);
          break;
        case 1:
          console.log("my friend2");
          this.$emit("player-status", 1, 25);
          this.$emit("curr-page", 5);
          break;
        case 2:
          console.log("my friend3");
          this.$emit("player-status", 1, 50);
          this.$emit("curr-page", 5);
          break;
        case 3:
          console.log("my friend4");
          this.$emit("player-status", 0, 75);
          this.$emit("curr-page", 5);
          break;
        case 4:
          console.log("my friend5");
          this.$emit("player-status", 0, 100);
          this.$emit("curr-page", 5);
          break;
        default:
      }
    },
  },
};
</script>

<style scoped>
#game_home {
  background-image: url("../assets/photos/GameBackground.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  /* left: 0%;
  top: 0%; */
  height: 100%;
  width: 100%;
  overflow: hidden;
  position: fixed;
}

#question_container {
  position: absolute;
  height: 25%;
  width: 72%;
  left: 13%;
  top: 6%;
  background-image: url("../assets/gameSymbols/GameQuestionBox.svg");
  background-size: cover;
  background-attachment: inherit;
}

#question {
  position: absolute;
  width: 95%;
  height: 85%;
  top: 5%;
  left: 2.5%;
  color: white;
  font-family: MyFont;
  font-weight: 1000vw;
  font-size: 4.2vw;
  text-align: center;
  line-height: 41px;
  direction: rtl;
}

#deactivate {
  pointer-events: none;
}

#choices_container {
  position: absolute;
  height: 50%;
  width: 75%;
  left: 9%;
  top: 37%;
}

#choices {
  position: relative;
  margin-bottom: 2.5%;
  background-image: url("../assets/gameSymbols/AnswerSymbol.svg");
  background-size: cover;
  background-repeat: no-repeat;
  width: 76%;
  height: 13%;
  direction: rtl;
  left: 11%;
  top: 40%;
}

#text_answer {
  position: absolute;
  color: white;
  width: 70%;
  height: 50%;
  right: 12%;
  top: 0%;
  font-family: MyFont;
  font-weight: 1000vw;
  font-size: 3.5vw;
  overflow-wrap: break-word;
  direction: rtl;
}

@font-face {
  font-family: MyFont;
  src: url("../assets/fonts/IBMPlexSansHebrew-Regular.ttf");
}

#check_button {
  position: absolute;
  text-align: end;
  font-weight: 1000vw;
  font-size: 6vw;
  color: white;
  bottom: -2%;
  display: none;
  border: 1mm solid rgb(255, 0, 200);
  left: 1%;
  height: 5%;
  width: 17%;
  background-color: rgb(255, 0, 200);
  border-radius: 8px;
  text-align: center;
}

#choices_box {
  height: 90%;
  width: 100%;
  left: 0%;
  top: 0%;
}
</style>