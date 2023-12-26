<template>
    <div id="stage3">
        <div v-show="numStage !== 7"
        class="img9">
            <select @click.once="form()" class="select1" >
                <option value="volvo">שדה חובה</option>
                <option  value="saab">רגילה/ הכרה</option>
            </select>
            <select @click.once="form()" class="select2">
                <option value="volvo">שדה חובה</option>
                <option value="saab">רגיל</option>
            </select>
            <label @click.once="form()" class="switch switch1">
                <input type="checkbox">
                <span class="slider round"></span>
            </label>
            <label @click.once="form()" class="switch switch2">
                <input type="checkbox">
                <span class="slider round"></span>
            </label>
            <div v-if="show5"  class="sum">סכום תווים עבור בקשה
                <input @input="form()" v-model="sum" type="number">
            </div>
            <div v-if="show5"  class="time">משך זכאות בחודשים
                <input @input="form()" v-model="time" type="number">
            </div>
        </div>

        <div v-if="showSummary" class="recommen" >
            <input type="textArea" v-model="recommendation" @click="toSummary(2)">
        </div>

        <img v-if="numStage === 9" class="approval" src="@/assets/Media/14.png" alt="">

        <img class="saveButton" v-if="(show6 && numStage !== 7) && (numStage !== 9)" src="@/assets/Media/shamur.png" alt="">
        <img @click="saveForm" class="saveButton" v-if="(!show6 && numStage !== 7) || numStage === 9" src="@/assets/Media/save.png" alt="">

        <div v-if="saved" class="darkScreen"></div>
        <div v-if="saved" class="containerDone">
            <img  src="@/assets/Media/15.png">
        </div>

        <span v-if="numStage === 6">
          <div class="documents" @click="nextStage"></div>
        </span>

        <Stage7 v-if="numStage===7" @nextStage="nextStage"></Stage7>

        <div v-if="numStage === 8">
            <div class="summary" @click="toSummary(1)"></div>
        </div>
    </div>
  </template>

  <script>
  import Stage7 from './Stage7.vue'
  export default {
    components: {Stage7},
    props: ['numStage'],
    name: "step3",
    data() {
      return {
        show5: false,
        show6: true,
        numTrueForm: 0,
        saved: false,
        showDocumentsPage: false,
        sum: 0,
        time:0,
        showSummary: false,
        recommendation: "",
      }
    },
    methods: {
        form() {
          this.numTrueForm+=1;
          if(this.numTrueForm >= 4){
            this.show5 = true;
            if (this.sum !== 0 && this.time !== 0 && this.sum > 299) {
              this.show6 = false;
            }
          }
        },
        saveForm() {
          this.saved = true;
          setTimeout(() => {
                this.$emit("nextStage");
                    this.show6 = true;
                    this.saved = false;
                    this.showSummary = false;
            }, 1500);
        },
        showDocuments() {
          this.showDocumentsPage = true;
        },
        nextStage() {
          this.$emit("nextStage");
        },
        toSummary(num) {
            if (num===1){
                this.showSummary = true;
            }
            else if (num===2 && this.recommendation !== undefined){
                console.log(this.recommendation);
                this.show6 = false;
            }
        }

    }
  }
  </script>
  
  
  <style scoped>
  #stage3{
    display: flex;
    align-items: center;
    flex-direction: column;
  }
.img9 {
  width: 44vw;
  height: 89.5vh;
  background-image: url("@/assets/Media/8.png");
  background-size: 100% 100%;
  
}
.select1 {
   position: absolute;
    top: 38.5vh;
    right: 36.5vw;
    width: 7.5vw;
    height: 2vh
}
.select2 {
  position: absolute;
  top: 38.5vh;
  right: 44.5vw;
  width: 7.5vw;
  height: 2vh;
}

.saveButton {
  width: 5vw;
  height: 3vh;
}

.sum {
  width: 15vw;
  position: absolute;
  top: 43vh;
  right: 36vw;
}
.time {
  width: 15vw;
  position: absolute;
  top: 43vh;
  right: 48vw;
}

.switch {
  position: relative;
  display: inline-block;
  width: 2.3vw;
  height: 1.6vh;
}
.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: .4s;
  transition: .4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 1.5vh;
  width: 1vw;
  right: 0vw;
  background-color: white;
  -webkit-transition: .4s;
  transition: .4s;
}

input:checked + .slider {
  background-color: #2196F3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196F3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(-2.3vh);
  -ms-transform: translateX(-2.3vh);
  transform: translateX(-2.3vh);
}

.slider.round {
  border-radius: 2vh;
}

.slider.round:before {
  border-radius: 50%;
}

.switch1 {
  position: absolute;
  top: 38.6vh;
  right: 53.5vw
}
.switch2 {
  position: absolute;
  top: 45.3vh;
  right: 29.5vw;
}

.containerDone {
  width: 98vw;
  height: 98vh;
  display: flex;
  position: absolute;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

.containerDone img {
  width: 20vw;
  height: 25vh;
}

.darkScreen { 
  position: absolute;
  width: 98vw;
  height: 100%;
  opacity: 65%;
  background-color: black;
}
.documents{
  position: absolute;
  top: 7vh;
  right: 34vw;
  width: 5vw;
  height: 2vh;
}

.img91 {
  width: 45vw;
  height: 98vh;
  background-image: url("@/assets/Media/18.png");
  background-size: 100% 100%;
}

.summary{
  position: absolute;
  top: 7vh;
  right: 40vw;
  width: 6vw;
  height: 2vh;
}
.recommen {
  width: 45vw;
  height: 8vh;
  background-image: url("@/assets/Media/23.png");
  background-size: 100% 100%;
}
.recommen input {
    position: absolute;
    top: 91.5vh;
    right: 31.5vw;
    width: 38.5vw;
    height: 5vh;
    border-radius: 1vh
}

.approval {
    width: 45vw;
    height: 25vh;
}
  </style>