<template>
    <div id="mainScreen">
            <div v-if="numStage===1 || numStage===10"  class="container1">
              <div>
                <div class="img1"></div>
                <div @click="nextStage()" v-if="showUser" class="user">
                    <p>{{name}}</p>
                </div>
                <input class="input1" type="text" v-model="name"  @keydown.enter="inputFun()"/>
              </div>
              <div class="img2"></div>
              <img class="reshima" src="@/assets/Media/reshima.png" @click="open(1)">
              <img v-if="show1" class="img3" src="@/assets/Media/16.png" alt="">
              <span v-if="show1">
                <div :class="show2? `rejection open` : `rejection`"  @click="open(2)"></div>
                <div class="openReason" @click="open(3)"></div>
                <img v-if="show3" class="img4" src="@/assets/Media/22.png" alt="">
                <div class="closeReason" @click="open(3)"></div>
              </span>
            </div>
            <stage2 v-if="numStage===2 || numStage===4 || numStage===5 || numStage===5" @nextStage="nextStage" :numStage="numStage" :name="name"></stage2>
            <stage3 v-show="numStage===3 || numStage===6 || numStage===7 || numStage===8 || numStage===9" @nextStage="nextStage" :numStage="numStage" ></stage3>
            <Stage6 v-if="numStage===5" @nextStage="nextStage"></Stage6>
        <div></div>
    </div>
</template>

<script>
import Stage2 from './Stage2.vue'
import Stage6 from './Stage6.vue'
import Stage3 from './Stage3.vue'

  export default {
    components: {Stage2, Stage6, Stage3},
    name: "mainScreen",
    data() {
      return {
        showUser: false,
        numStage: 1,
        name: "",
        show1: false,
        show2: false,
        show3: false,
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
          console.log(this.numStage);
        },
        open (num) {
          if (num === 1){
            this.show1 = true;
          }
          else if (num === 2){
            this.show2 = true;
          }
          else if (num === 3){
            this.show3 = !this.show3;
          }
        }
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
  right: 0.1vw;
  background-color: #8585ad;
  border-radius: 5vh;
  border-color: #8585ad;
  width: 13.5vw;
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
.reshima {
    width: 4vw;
    height: 4vh;
    position: absolute;
    top: 13.5vh;
    right: 41.4vw;
}

.img3 {
    width: 26vw;
    height: 85vh;
    position: absolute;
    top: 13vh;
    right: 20vw;
}
.rejection {
    width: 22vw;
    height: 20vh;
    position: absolute;
    top: 25vh;
    right: 22vw;
}

.open {
  background-image: url("@/assets/Media/21.png");
  background-size: 120% 100%;
}

.openReason {
    width: 5vw;
    height: 4vh;
    position: absolute;
    top: 35vh;
    right: 39vw;
}

.img4 {
    width: 22vw;
    height: 20vh;
    position: absolute;
    top: 35vh;
    right: 22vw;
}
.closeReason {
  width: 5vw;
    height: 4vh;
    position: absolute;
    top: 37vh;
    right: 39vw;
}

</style>
