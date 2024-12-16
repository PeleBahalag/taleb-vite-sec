<template>
  <div id="main_text">
    <div id="back_button" @click="backButton"></div>
    <div id="next_button" @click="nextButton"></div>
    <div id="next_chapter" @click="nextChapter">לעבור לפרק הבא</div>
    <div id="last_chapter" @click="lastChapter">לפרק הקודם</div>
    <div id="first_chapter">זה הוא הפרק הראשון</div>
    <div id="final_chapter">זה הוא הפרק האחרון</div>
    <h3 id="inner_title">{{ this.nameTitle }}</h3>
    <img
      src="../assets/symbols/GraphicThree.svg"
      class="graphics"
      id="graphics_moving"
      v-if="choosen === 0 && i === 1 && j === 2"
    />
    <img
      src="../assets/symbols/GraphicFour.svg"
      class="graphics"
      id="graphics_moving"
      v-if="choosen === 1 && i === 2 && j === 1"
    />
    <img
      src="../assets/symbols/GraphicFive.svg"
      class="graphics"
      id="graphics_moving"
      v-if="choosen === 1 && i === 1 && j === 2"
    />
    <img
      src="../assets/photos/ThreePointOneOne.png"
      class="graphics"
      v-if="choosen === 1 && i === 0 && j === 0"
    />
    <img
      src="../assets/photos/ThreePointOneTwo.png"
      class="graphics"
      v-if="choosen === 1 && i === 0 && j === 1"
    />
    <img
      src="../assets/photos/ThreePointThree.png"
      class="graphics"
      v-if="choosen === 1 && i === 1 && j === 0"
    />
    <img
      src="../assets/photos/ThreePointFour.png"
      class="graphics"
      v-if="choosen === 1 && i === 2 && j === 9"
    />
    <img
      src="../assets/photos/FourPointOne.png"
      class="grphics"
      v-if="choosen === 2 && i === 0 && j === 0"
    />
    <img
      src="../assets/photos/FourPointOneTwo.png"
      class="grphics"
      v-if="choosen === 2 && i === 0 && j === 2"
    />
    <img
      src="../assets/photos/FourPointFour.png"
      class="other_graphics"
      v-if="choosen === 2 && i === 2 && j === 1"
    />
    <div id="study" v-if="choosen === 0">
      <p id="real_study_text" v-html="arrayTwo[i][j]"></p>
    </div>
    <div id="study" v-if="choosen === 1">
      <p id="real_study_text" v-html="arrayThree[i][j]"></p>
    </div>
    <div id="study" v-if="choosen === 2">
      <p id="real_study_text" v-html="arrayFour[i][j]"></p>
    </div>
  </div>
</template>


<script>
export default {
  name: "main-text",
  props: ["subjectsName", "subNumber", "innerPart", "nameTitle"],
  data() {
    return {
      arrayTwo: [
        [
          "מבחן הוא כלי המאפשר למפקדים להעריך את רמת הידע, ההבנה והכשירות של חניך במהלך ההכשרה.<br> התארגנות טרם מבחן: <br> טרם המבחן יש לפרסם לחניכים את  הנושאים עליהם הם עתידים להיבחן. במבחן מעשי נדרש לפרסם לחניכים את דף ההערכה טרם המבחן, יש לאפשר לחניכים זמן ללמידה עצמית טרם הבחינה.",
          "פיתוח המבחן:<br> פיתוח המבחן ייעשה בהתאם לתורה המקצועית בנושא כתיבת מבחנים,<br> לכל מבחן עיוני ייבנה טופס תשובות (תשובון), <br>לכל מבחן מעשי ייבנה דף הערכה אשר יכלול את הקריטריונים להערכת הביצוע של הנבחן. ואת אופן חלוקת המשקלים הפנימית.",
          'בדיקה ומישוב המבחן:<br> בדיקה של המבחן תיעשה ביחס לדף התשובות המאושר, במבחן עיוני יש לפרסם את דף התשובות עם חלוקת הטפסים הבדוקים,<br> במבחן מעשי, יש לבצע משוב פרונטלי/כתוב לכל נבחן ע"ב דף ההערכה עד שבוע מיום הבחינה.<br> יש לקיים שיחה אישית עם חניך הנכשל במבחן עיוני/מעשי בה יוסברו לחניך נקודות הכשל והמשך תהליך הלמידה.',
          "*המבחנים העיוניים לא יעלו על 30% סך המבחנים המסמיכים בהכשרה.<br> *לכל חניך יינתנו שני מועדים לביצוע המבחן - מועד א’ ומועד ב.",
        ],
        [
          "תיק הכולל את התוכן המקצועי והפעולות ההדרכתיות, המרכיבות שיעור פרונטלי או פעילות בעלת מרכיבים מעשיים.<br> התיק נועד לאפשר הכנה מקצועית של המפקד או מדריך, להביא לאחידות מקצועית ולתרום לזיכרון הארגוני.",
          'כתיבה ותיקוף של תיק מדריך: <br> לכל יחידת לימוד יבוצעו תהליך פיתוח הדרכתי ע"פ התו"ל, לכל יחידת לימוד מסוג עיוני או מעשי ייכתב תיק מדריך, על כל יחידת לימוד יהיה חתום קצין בדרגת סגן לפחות',
          "",
        ],
      ],

      arrayThree: [
        ["", ""],
        [
          "",
          "הגדרות:  סגל הדרכה - כל בעל תפקיד המשתייך למסגרת המבצעת את ההדרכה בפועל. הכנת סגל - תהליך של בניית סגל כצוות עבודה. התוכנית להכנת סגל תיבנה ע”י, מפקד הפלוגה או מפקד הקורס בדרגת סגן לכל הפחות.",
          "",
          "סיכום הכנת הסגל: לכל הכנת סגל יתבצע סיכום בראשות מפקד הפלוגה או מפקד ההכשרה.  כחלק מהסיכום יש לבצע תחקור והפקת לקחים בשיתוף כלל אנשי הסגל. במהלך ההכשרה יוקדש פרק לתחקור והפקות לקחים שבוצעה טרם המחזור ובמהלכה.",
        ],
        [
          "הערכת איש הסגל היא תהליך שיטתי ומובן  המאורגן בתוכנית קבועה מראש. תהליך הערכת וחניכת איש סגל מתחילה מיום קליטתו כאיש סגל ועד לסיום תפקידו.",
          "",
          'שיטה:<br> 16.בניית תכנית הערכה לאיש סגל:<br> א.לכל איש סגל תיבנה תכנית חניכה והערכה אחת למחזור <br> ב.תכנית ההערכה והחניכה תיבנה ע"ב אבחון של מפקדי המוערך/נחנך.<br> ג.תכנית ההערכה והחניכה תוצג לאיש הסגל בשבוע הראשון של הכנת הסגל. <br> ד.תכנית ההערכה והחניכה תכלול מבחנים מסמיכים ומופעי חניכה.',
          '17.מימוש ובקרה<br> א.ניהול המערכת החונכת יבוצע ע"י המ"פ. הוא הנושא באחריות לכך שלכל איש סגל בפלוגה תיכתב תכנית הערכה וחניכה.<br> ב.בקרה-תבוצע ע"י המ"פ וקצינות הצפ"ה בגדודים.',
          "18.מופעי וכלי הערכה וחניכה<br> א.מבחן רמה מקצועי-מבחן מקצועי יתבצע אחת לארבעה חודשים או אחת למחזור(הקצר מבין השניים). מבחן הרמה יהיה מעשי ועיוני ויכלול את הידע המקצועי אשר נדרש ממפקד בהכשרה. מבחן הרמה מהווה את שמירת הכשירות המקצועית. מבחן זה יתקיים במהלך הכנת הסגל ויהווה תנאי לפתיחת המחזור.",
          'ב.בוחן כושר גופני-אחת לחודשיים או אחת למחזור(הקצר מבין שניים) יתקיים בוחן כש"ג אשר יכלול את ההישג הנדרש לאיש הסגל בתחום הכושר הגופני. בוחן זה יתקיים במהלך הכנת הסגל ויהווה תנאי לפתיחת מחזור.',
          "ג.בוחן הדרכה-אחת לחודשיים או אחת למחזור(הקצר מבין השניים) יוערך המפקד על יכולותיו בביצוע תהליכי חניכה והערכת חיילים, ועל יכולותיו להעביר שיעור. מבחן זה יתקיים במהלך הכנת הסגל ויהיה תנאי לפתיחת מחזור.",
          'ד.משוב מפקד(מופע חניכה)- אחת לחודשיים או פעמיים במחזור הכשרה יבצע המפקד הממונה על איש הסגל, תצפית סדורה במופע פורמאלי שמוביל איש הסגל המוערך כגון- הובלת תרגיל, הובלת מסדר, ביצוע תדריך, העברת שיעור וכיו"ב. לפחות מופע חניכה אחד במחזור יהיה "חניכה על חניכה", כלומר, מישוב על האופן בו המפקד חונך את חייליו.',
          ' ה.חוו"ד תקופתי של מפקד ישיר- במהלך כל תקופת תפקידו יחנך המפקד על-ידי מפקדו הישיר באופן פורמלי(כמתואר בסעיף הקדום) ובאופן בלתי פורמאלי על תפקידו כמפקד-"חניכה לתפקיד". אחד לחודשיים או אחד למחזור(הקצר מבין השניים) ימלא ויעביר מפקדו הישיר של איש הסגל חוות דעת. חוות הדעת. חוות הדעת תכלול מדדים קבועים ואובייקטיבים בנושאים הבאים: מקצועיות, פיקוד, הדרכה וערכים. חוות הדעת תהיה מבוססת על כלל הכלים שפורטו בסעיף זה וכן כלים נוספים כגון חוו"ד עמיתים ומשוב חניכים.',
          "",
        ],
      ],

      arrayFour: [
        [
          "",
          "<p>חייל יכול להתקשות בתחומים הבאים: שפה, כושר, קליעה, תוכן מקצועי או בכל תחום אחר שבו ההכשרה נוגעת. דרכי הפעולה לקידום החניך: <br> - שעות תגבור <br> -זמנים ללמידה עצמית <br> -מועדי מבחנים חוזרים <br> -התנסויות <br> -והצמדת חונך מקצועי</p>",
        ],
        [
          "תהליך בחירת חניך מצטיין וחניך למופת מעודדת מצוינות ומאפשרת להדגיש את ההתנהגות וההישגים הרצויים בהכשרה. תהליך בחירת חניך מצטיין וחניך למופת נועד להגביר את הרצון להשקיע בהכשרה ולתגמל חניכים שהשקיעו בהכשרה ושהגיעו להישגים שבולטים לטובה.",
          "<p>להלן קריטריונים תומכים לבחירת חניך מצטיין וחניך למופת. <br> חניך מצטיין: <br> ציונים גבוהים - ציון סופי מעל 80, חו''ד מפקד בולט לחיוב, ללא אירועי משמעת משמעותיים, סוציומטרי עמיתים גבוה(במידה וקיים) ותכונותיו העיקריות אשר יבואו לידי ביטוי הן: <br> חתירה למצוינות, יוזמה, עזרה לזולת והתמדה.</p>",
          "<p>חניך למופת: <br> חו''ד מפקד בולט לחיוב, ללא אירועי משמעת משמעותיים, סוציומטרי עמיתים גבוה(במידה וקיים), תכונותיו העיקריות אשר יבואו לידי ביטוי הינן:<br>השקעה, יוזמה, עזרה לזולת, התמדה, למידה והשתפרות.</p>",
        ],
        [
          "תיק אישי לחניך משמש אמצעי לאיסוף המידע וריכוזו במכלול נושאים בעלי רלוונטיות לחניכים בקורס. הוא מהווה מעקב מסודר ושיטתי ומאפשר איתור מוקדם של בעיות לימודיות, חברתיות ואישיות.",
          "",
        ],
      ],

      choosen: this.subNumber,
      i: this.innerPart,
      j: 0,
      graphicsArray: [[]],
    };
  },
  methods: {
    startPage() {
      this.$emit("curr-page", 2);
    },

    backButton() {
      document.getElementById("next_button").style.display = "block";
      document.getElementById("first_chapter").style.display = "none";
      document.getElementById("next_chapter").style.display = "none";
      document.getElementById("final_chapter").style.display = "none";
      if (this.j > 0) {
        this.j = this.j - 1;
      } else if (this.j <= 0) {
        this.lastChapter();
      }
    },

    nextButton() {
      document.getElementById("back_button").style.display = "block";
      document.getElementById("first_chapter").style.display = "none";
      document.getElementById("last_chapter").style.display = "none";

      if (this.choosen === 0) {
        if (this.arrayTwo[this.i][this.j + 1] === undefined) {
          if (this.arrayTwo[this.i + 1] === undefined) {
            document.getElementById("final_chapter").style.display = "block";
            document.getElementById("next_button").style.display = "none";
          } else {
            document.getElementById("next_chapter").style.display = "block";
            document.getElementById("next_button").style.display = "none";
          }
        } else {
          document.getElementById("next_button").style.display = "block";
          this.j = this.j + 1;
        }
      } else if (this.choosen === 1) {
        if (this.arrayThree[this.i][this.j + 1] === undefined) {
          if (this.arrayThree[this.i + 1] === undefined) {
            document.getElementById("final_chapter").style.display = "block";
            document.getElementById("next_button").style.display = "none";
          } else {
            document.getElementById("next_chapter").style.display = "block";
            document.getElementById("next_button").style.display = "none";
          }
        } else {
          document.getElementById("next_button").style.display = "block";
          this.j = this.j + 1;
        }
      } else {
        if (this.arrayFour[this.i][this.j + 1] === undefined) {
          if (this.arrayFour[this.i + 1] === undefined) {
            document.getElementById("final_chapter").style.display = "block";
            document.getElementById("next_button").style.display = "none";
          } else {
            document.getElementById("next_chapter").style.display = "block";
            document.getElementById("next_button").style.display = "none";
          }
        } else {
          document.getElementById("next_button").style.display = "block";
          this.j = this.j + 1;
        }
      }
    },

    nextChapter() {
      console.log(this.i);
      this.$emit("make-progress", this.i);
      this.i = this.i + 1;
      this.j = 0;
      document.getElementById("next_button").style.display = "block";
      document.getElementById("next_chapter").style.display = "none";
    },

    lastChapter() {
      console.log("hi");
      if (this.i === 0) {
        console.log("hello");
        document.getElementById("back_button").style.display = "none";
        document.getElementById("first_chapter").style.display = "block";
      } else {
        this.$emit("made-progress", this.i);
        this.i = this.i - 1;
        this.j = 0;
        document.getElementById("last_chapter").style.display = "none";
        document.getElementById("back_button").style.display = "block";
      }
    },
  },
};
</script>


<style>
#main_text {
  background-image: url("../assets/symbols/TextBackground.svg");
  background-size: cover;
  background-repeat: no-repeat;
  visibility: visible;
}
@font-face {
  font-family: MyFont;
  src: url("../assets/fonts/IBMPlexSansHebrew-Regular.ttf");
}

#study {
  position: absolute;
  width: 100%;
  height: 90%;
  cursor: pointer;
  bottom: 10%;
  direction: rtl;
    color: white;
  font-family: MyFont;
  font-weight: 700vw;
  font-size: 4.3vw;
}

#real_study_text {
  position: absolute;
    direction: rtl;
  width: 95%;
  height: 80%;
  line-height: 2;
  top: 10%;
  right: 2%;
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

#next_chapter {
  position: absolute;
  width: 30%;
  height: 10%;
  bottom: 0%;
  left: 2%;
  cursor: pointer;
  display: none;
  color: white;
  font-family: MyFont;
}

#last_chapter {
  position: absolute;
  width: 30%;
  height: 10%;
  bottom: 0%;
  right: 2%;
  cursor: pointer;
  display: none;
  color: white;
  font-family: MyFont;
}

#first_chapter {
  position: absolute;
  width: 30%;
  height: 10%;
  bottom: 0%;
  right: 2%;
  cursor: pointer;
  display: none;
  color: white;
  font-family: MyFont;
}

#final_chapter {
  position: absolute;
  width: 30%;
  height: 10%;
  bottom: 0%;
  left: 2%;
  cursor: pointer;
  display: none;
  color: white;
  font-family: MyFont;
}

#inner_title {
  position: absolute;
  height: 10%;
  width: 100%;
  color: white;
   font-family: MyFont;
  font-weight: 700vw;
  font-size: 4.5vw;
  direction: rtl;
  right: 0%;
  top: -2%;
}

.graphics {
  position: absolute;
  height: 85%;
  width: 90%;
  left: 10%;
  top: 5%;
}

.other_graphics {
  position: absolute;
  height: 75%;
  width: 82%;
  left: 10%;
  top: 5%;
}

@keyframes graphicsMovie {
  from {
    top: -100%;
  }
  to {
    top: 5%;
  }
}

#graphics_moving {
  animation: graphicsMovie 2s linear;
}
</style>