<template>
    <div id="stage3">
        <div  class="img9">
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
        <img class="saveButton" v-if="show6" src="@/assets/Media/shamur.png" alt="">
        <img @click="saveForm" class="saveButton" v-if="!show6" src="@/assets/Media/save.png" alt="">
        <div v-if="saved" class="darkScreen" ></div>
        <div v-if="saved" class="containerDone">
            <img  src="@/assets/Media/15.png">
        </div>

        <span v-if="numStage !== 6">
          <div class="documents"></div>
        </span>
        
    </div>
  </template>

  <script>
export default {
    props: ['numStage'],
    name: "stage3",
    // props: ['numStage'],
    data() {
      return {
        show5: false,
        show6: true,
        numTrueForm: 0,
        saved: false,
        
      }
    },
    methods: {
        form() {
          this.numTrueForm+=1;
          if(this.numTrueForm >= 4){
            this.show5 = true;
            if (this.sum !== undefined && this.time !== undefined && this.sum > 299) {
              this.show6 = false;
            }
          }
        },
        saveForm() {
          this.saved = true;
          setTimeout(() => {
            this.saved = false;
            this.$emit("nextStage");
            }, 1500);
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
  .container3{
  display: flex;
  align-items: center;
  flex-direction: column;
}
.img9 {
  width: 45vw;
  height: 95vh;
  background-image: url("@/assets/Media/8.png");
  background-size: 100% 100%;
  
}

.select1 {
  position: fixed;
  top: 38vh;
  right: 37vw;
  width: 7vw;
}

.select2 {
  position: fixed;
  top: 38vh;
  right: 45.5vw;
  width: 7vw;
}

.saveButton {
  width: 5vw;
  height: 3vh;
}

.sum {
  width: 15vw;
  position: fixed;
  top: 43vh;
  right: 36vw;
}
.time {
  width: 15vw;
  position: fixed;
  top: 43vh;
  right: 48vw;
}

.switch {
  position: relative;
  display: inline-block;
  width: 2.3vw;
  height: 1.5vh;
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
  top: 38.5vh;
  right: 53.4vw;
}
.switch2 {
  position: absolute;
  top: 45vh;
  right: 29.3vw;
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
  height: 98vh;
  background-color: black;
  opacity: 65%;
}
.documents{
  position: absolute;
  top: 7vh;
  right: 7vw;
  width: 5vw;
  height: 2vh;
  background-color: black;
}
  </style>