<template>
    <div id="main">
        <!-- <div> -->
            <div v-if="numStage===1" class="container1">
              <div>
                <div class="img1"></div>
                <div @click="nextStage()" v-if="showUser" class="user">
                    <p>{{name}}</p>
                </div>
                <input class="input1" type="text" v-model="name"  @keydown.enter="inputFun()"/>
              </div>
              <div class="img2"></div>
            </div>
            <stage2 v-if="numStage===2 || numStage===4 || numStage===5 || numStage===5" @nextStage="nextStage" :numStage="numStage" :name="name"></stage2>
            <stage3 v-show="numStage===3 || numStage===6" @nextStage="nextStage" :numStage="numStage" ></stage3>
            <Stage6 v-if="numStage===5" @nextStage="nextStage"></Stage6>
        <!-- </div> -->
        <div></div>
    </div>
</template>

<script>
import Stage2 from './Stage2.vue'
import Stage3 from './stage3.vue'
import Stage6 from './Stage6.vue'
  export default {
    components: {Stage2, Stage3, Stage6},
    name: "main",
    data() {
      return {
        showUser: false,
        numStage: 3,
        numMis: 0,
        showRequest: false,
        show3: false,
        show4: false,
        show5: false,
        show6: true,
        numTrueForm: 0,
        saved: false
      }
    },
    methods: {
      inputFun() {
          if (this.name !== undefined){
              this.showUser = true;
          }
        },
        nextStage() {
          this.numStage += 1;
          // if (this.numStage >= 4) {
          //   this.saved = false;
          //   console.log(this.saved);
          // }
          console.log(this.numStage);
        },
        // requestShow() {
        //   this.showRequest = true;
        // },
        // toShow3() {
        //   this.show3 = true;
        //   this.showRequest = false;
        // },
        // form() {
        //   this.numTrueForm+=1;
        //   if(this.numTrueForm >= 4){
        //     this.show5 = true;
        //     if (this.sum !== undefined && this.time !== undefined && this.sum > 299) {
        //       this.show6 = false;
        //     }
        //   }
        // },
        // saveForm() {
        //   this.saved = true;
        //   setTimeout(() => {
        //         this.nextStage();
        //     }, 1500);
        // }
    },
    computed: {
    }
  }
  </script>

<style scoped>
.img1 {
  height: 98vh;
  width: 20vw;
  background-image: url("@/assets/Media/39.png");
  background-size: 100% 100%;
  position: relative;
  z-index: -1;
}

.img2 {
  height: 98vh;
  width: 80vw;
  background-image: url("@/assets/Media/20.png");
  background-size: 100% 100%;
  position: relative;
  z-index: -1;
}

.input1 {
  position: relative;
  bottom:88vh;
  right: 0.2vw;
  background-color: #8585ad;
  border-radius: 20%;
  border-color: #8585ad;
  width: 13vw;
  height: 2.3vh;
}

.container1 {
  display: flex;
  height: 98vh;
  position: relative;
  top: 0vh;
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
  height: 98vh;
}

.container2 {
  display: flex;
}

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
  right: 22vw;
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

/* .termsService{
  width: 27vw;
  height: 13vh;
  position: fixed;
  bottom: 45vh;
  right: 70vw;
} */
</style>
