<template>
    <div id="stage7">
        <div class="img91"></div> 
        <div class="container document" @click="toShow(1)">
            <div class="object"></div>
            <div class="object"></div>
            <div class="object"></div>
            <div class="object"></div>
            <div class="object"></div>
            <div class="object"></div>
        </div>
        <div class="container butza">
            <select v-model="choice1"  class="select" @click="checkDone(choice1)">
                <option>בוצע</option>
                <option>טרם בוצע</option>
                <option>לא יבוצע</option>
                <option>לא רלוונטי </option>
                <option>נדרש להשלמה</option>
                <option>מסמך לא תקין</option>
            </select>
            <select v-model="choice2"  class="select" @click="checkDone(choice2)">
                <option>בוצע</option>
                <option>טרם בוצע</option>
                <option>לא יבוצע</option>
                <option>לא רלוונטי </option>
                <option>נדרש להשלמה</option>
                <option>מסמך לא תקין</option>
            </select>
            <select v-model="choice3"  class="select" @click="checkDone(choice3)">
                <option>בוצע</option>
                <option>טרם בוצע</option>
                <option>לא יבוצע</option>
                <option>לא רלוונטי </option>
                <option>נדרש להשלמה</option>
                <option>מסמך לא תקין</option>
            </select>
            <select v-model="choice4"  class="select" @click="checkDone(choice4)">
                <option>בוצע</option>
                <option>טרם בוצע</option>
                <option>לא יבוצע</option>
                <option>לא רלוונטי </option>
                <option>נדרש להשלמה</option>
                <option>מסמך לא תקין</option>
            </select>
            <select v-model="choice5"  class="select" @click="checkDone(choice5)">
                <option>בוצע</option>
                <option>טרם בוצע</option>
                <option>לא יבוצע</option>
                <option>לא רלוונטי </option>
                <option>נדרש להשלמה</option>
                <option>מסמך לא תקין</option>
            </select>
            <select v-model="choice6"  class="select" @click="checkDone(choice6)">
                <option>בוצע</option>
                <option>טרם בוצע</option>
                <option>לא יבוצע</option>
                <option>לא רלוונטי </option>
                <option>נדרש להשלמה</option>
                <option>מסמך לא תקין</option>
            </select>
        </div>

        <img class="saveButton" v-if="!done" src="@/assets/Media/shamur.png">
          <img @click="toShow(2)" class="saveButton" v-if="done" src="@/assets/Media/save.png">

        <div v-if="showDoc" class="darkScreen" ></div>
        <div v-if="showDoc" class="containerDone">
            <img class="doc"  src="@/assets/Media/26.png">
            <div  @click="toShow(1)" class="bitul"></div>
        </div>

        <div v-if="showDone" class="darkScreen" ></div>
        <div v-if="showDone" class="containerDone">
            <img class="done"  src="@/assets/Media/15.png">
        </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "stage7",
    data() {
      return {
        showDoc: false,
        choice1: "",
        choice2: "",
        choice3: "",
        choice4: "",
        choice5: "",
        choice6: "",
        numChoiceButza: 0,
        showDone: false,
        done: false
      }
    },
    methods: {
        toShow(num) {
            console.log(num);
            if (num === 1) {
                this.showDoc = !this.showDoc;
            }
            else if (num === 2) {
                this.showDone = !this.showDone;
                setTimeout(() => {
                    this.$emit("nextStage");
                    this.showDone = !this.showDone;
                }, 1500);
            }
        },
        checkDone(choise) {
        if (choise === "בוצע") {
                this.numChoiceButza += 1;
                console.log(this.numChoiceButza);
            if (this.numChoiceButza === 6) {
                this.done = true;
            }
            }
        }
    },
    computed: {
  
    }
  }
  </script>
  
  <style scoped>
  #stage7{
    display: flex;
    align-items: center;
    flex-direction: column;
  }
  .img91 {
  width: 45vw;
  height: 100vh;
  background-image: url("@/assets/Media/18.png");
  background-size: 100% 100%;
}

.container{
    width: 10vw;
    height: 50vh;
    /* background-color: bisque; */
    position: absolute;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    top: 35vh;
}
.object {
    width: 7vw;
    height: 5vh;
}
.document {
    right: 30vw;
    cursor: pointer;
}
.butza {
    left: 27vw
}
.darkScreen { 
  position: absolute;
  width: 98vw;
  height: 100vh;
  background-color: black;
  opacity: 65%;
}

.containerDone {
  width: 98vw;
  height: 100vh;
  display: flex;
  position: absolute;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

.bitul{
    width: 7vw;
    height: 3vh;
    position: absolute;
    right: 42vw;
    top: 67vh;
    cursor: pointer;
}
.doc {
    width: 30vw;
    height: 45vh;
}

.done {
    width: 20vw;
    height: 25vh;
}
.saveButton {
    width: 4.5vw;
    height: 3vh;
    position: absolute;
    top: 95.4vh;
    right: 62.9vw;
    cursor: pointer;
}

.select {
    width: 7vw;
    height: 3vh;
    cursor: pointer;
}
  </style>