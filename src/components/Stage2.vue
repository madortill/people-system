<template>
    <div id="stage2">
        <div>
            <div class="img1">
                <div class="user">
                    <p>{{name}}</p>
                </div>
            </div>
            <input class="input1" type="text" @keydown.enter="findUser"/>
        </div>
        <div class="partIn2">
            <img class="img3" src="@/assets/Media/5.png" alt="">
            <img class="img4" src="@/assets/Media/3.png" alt="">
            <div class="plus" @click="requestShow()"></div>
            <img  v-if="showRequest" class="img6" src="@/assets/Media/19.png" alt="">
            <div  v-if="showRequest" class="createRequest" @click="toShow3()"></div>
            <img v-if="numStage===2" class="img5" src="@/assets/Media/2.png" alt="">
            <img v-if="numStage >= 4" class="img5" src="@/assets/Media/37.png" alt="">
            <div v-if="numStage >= 4" class="termsService" @click="nextStage()"></div>
        </div>
        <span v-if="numStage !== 4">
            <img v-if="show3" class="img7" src="@/assets/Media/6.png" alt="">
            <input v-if="show3" class="input2" type="text" placeHolder="בחר בקשה" v-model="request" @keydown.ס="inputFun()">
            <img v-if="show4" class="img8" src="@/assets/Media/7.png" alt="">
            <div v-if="show4" class="chooseRequest" @click="nextStage()" ></div>
        </span>
        <!-- <span v-if="numStage === 5">

        </span> -->
    </div>
  </template>

  <script>
export default {
    props: ['numStage', `name`],
    name: "stage2",
    data() {
      return {
        showRequest: false,
        show3: false,
        show4: false,
        request: ""
      }
    },
    methods: {
        inputFun() {
              this.show4 = true;
        },    
        nextStage() {
          this.$emit("nextStage");
        },
        requestShow() {
          this.showRequest = true;
        },
        toShow3() {
          this.show3 = true;
          this.showRequest = false;
        },
    }
  }
  </script>
  
  
  <style scoped>
  #stage2 {
    display: flex;
  }
  .img1 {
  height: 100vh;
  width: 20vw;
  background-image: url("@/assets/Media/39.png");
  background-size: 100% 100%;
  position: relative;
  z-index: -1;
}

.img2 {
  height: 100vh;
  width: 80vw;
  background-image: url("@/assets/Media/20.png");
  background-size: 100% 100%;
  position: relative;
  z-index: -1;
}

.input1 {
  position: relative;
  bottom:89vh;
  right: 0.1vw;
  background-color: #8585ad;
  border: none;
  border-radius: 5vh;
  width: 13.5vw;
  height: 2.3vh;
}
  .user {
  height: 10vh;
  width: 19vw;
  background-image: url("@/assets/Media/38.png");
  background-size: 100% 100%;
  position: fixed;
  bottom: 74vh;
  right: 1.5vh;
} 

.user p {
  color: #005ce6;
  position: relative;
  top: 25%;
  right: 21%;
}

.partIn2 {
  width: 80vw;
  height: 100vh;
}

/* .container2 {
  display: flex;
} */

.img3 {
  width: 79vw;
  height: 19vh;
}
.img4 {
  width: 20vw;
  height: 79vh;
}
.img5 {
  width: 59vw;
  height: 79vh;
}
.plus {
  background-image: url("@/assets/Media/PLUS.png");
  background-size: 100% 100%;
  width: 4vw;
  height: 7vh;
  position: fixed;
  bottom: 73vh;
  right:37vw;
  cursor: pointer;
}
.img6 {
  position: fixed;
  bottom: 36vh;
  right: 37vw;
}
.createRequest {
  width: 9vw;
  height: 5vh;
  position: fixed;
  bottom: 52vh;
  right: 39vw;
  cursor: pointer;
}
.img7{
  width: 95vw;
  height: 95vh;
  position: fixed;
  bottom: 2.5vh;
  right: 2.5vw;
}

.input2{
  width: 18vw;
  height: 3vh;
  position: fixed;
  bottom: 85.5vh;
  right: 22.5vw;
  background-color: #cccccc;
}

.img8{
  width: 20vw;
  height: 18vh;
  position: fixed;
  bottom: 67vh;
  right: 22vw;
}
.chooseRequest{
  width: 20vw;
  height: 6vh;
  position: fixed;
  bottom: 73vh;
  cursor: pointer;
  right: 22vw;
}

.termsService{
  width: 27vw;
  height: 13vh;
  position: fixed;
  bottom: 45vh;
  right: 70vw;
  cursor: pointer;
}
  </style>