<template>
    <div id="main">
        <div>
            <div v-if="numStage===1" class="container1">
              <div>
                <div class="img1"></div>
                <div @click="nextStage()" v-if="showUser" class="user">
                    <p>{{name}}</p>
                </div>
                <input class="input1" type="text" v-model="name"  @keydown.enter="inputFun(1)"/>
              </div>
              <div class="img2"></div>
            </div>

            <div v-if="numStage===2" class="container2">
              <div>
                <div class="img1">
                  <div class="user">
                    <p>{{name}}</p>
                  </div>
                </div>
                <input class="input1" type="text" v-model="name"  @keydown.enter="findUser"/>
              </div>
              <div class="partIn2">
              <img class="img3" src="@/assets/Media/5.png" alt="">
              <img class="img4" src="@/assets/Media/3.png" alt="">
              <div class="plus" @click="request()"></div>
              <img  v-if="showRequest" class="img6" src="@/assets/Media/19.png" alt="">
              <div  v-if="showRequest" class="createRequest" @click="toShow3()"></div>
              <img class="img5" src="@/assets/Media/2.png" alt="">
            </div>
            <img v-if="show3" class="img7" src="@/assets/Media/6.png" alt="">
            <input v-if="show3" class="input2" type="text" value="בחר בקשה" v-model="request" @keydown.ס="inputFun(2)">
            <img v-if="show4" class="img8" src="@/assets/Media/7.png" alt="">
            <div v-if="show4" class="chooseRequest" @click="nextStage()" ></div>
            </div>

            <div v-if="numStage===3" class="container3">
              <!-- <img class="img9" src="@/assets/Media/8.png" alt=""> -->
              <div class="img9">
                <select @click.once="form(1)" class="select1" name="cars">
                  <option value="volvo">שדה חובה</option>
                  <option  value="saab">רגילה/ הכרה</option>
                </select>
                <select @click.once="form(2)" class="select2" name="cars">
                  <option value="volvo">שדה חובה</option>
                  <option value="saab">רגיל</option>
                </select>
                <div v-if="show5" @click="form(3)" class="sum">סכום תווים עבור בקשה
                  <input v-model="sum" type="number">
                </div>
                <div v-if="show5" @click="form(4)" class="time">משך זכאות בחודשים
                  <input v-model="time" type="number">
                </div>
              </div>
              <img class="saveButton" v-if="show6" src="@/assets/Media/shamur.png" alt="">
              <img class="saveButton" v-if="!show6" src="@/assets/Media/save.png" alt="">
            </div>
        </div>
        <div></div>
    </div>
</template>

<script>
  export default {
    name: "main",
    data() {
      return {
        showUser: false,
        numStage: 1,
        numMis: 0,
        showRequest: false,
        show3: false,
        show4: false,
        show5: false,
        show6: true,
        numTrueForm: 0
      }
    },
    methods: {
      inputFun(num) {
        if(num===1) {
          if (this.name !== undefined){
              this.showUser = true;
          }
        }
        else if(num===2) {
              this.show4 = true;
              console.log("ס");
        }
        },
        nextStage() {
          this.numStage += 1;
          console.log(this.numStage);
        },
        request() {
          this.showRequest = true;
        },
        toShow3() {
          this.show3 = true;
        },
        form(num) {
          console.log(num);
          console.log(this.sum);
          console.log(this.time);
          this.numTrueForm+=1;
          console.log(this.numTrueForm);
          if(this.numTrueForm === 2){
            this.show5 = true;
            if (this.sum !== undefined && this.time !== undefined && this.sum > 299) {
              console.log(this.show6);
              this.show6 = false;
            }
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

p {
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

</style>
