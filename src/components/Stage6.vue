<template>
    <div id="stage6">
        <div class="img1">
            <p class="date">27.112023</p>
            <p class="days">30</p>
            <p class="treatment">לא נמצא גורם מטפל</p>
            <div class="open" @click="nextStage"></div>
        </div>
    </div>
  </template>

  <script>
export default {
    name: "stage6",
    data() {
      return {
        show: false,
      }
    },
    methods: {
        nextStage() {
          this.$emit("nextStage");
        },
    }
  }
  </script>
  
  
  <style scoped>
  #stage6 {
    position: fixed;
    width: 98vw;
    height: 98vh;
    top: 1vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .img1 {
    width: 85vw;
    height: 85vh;
    background-image: url("@/assets/Media/11.png");
    background-size: 100% 100%;
  }

  p {
    position: fixed;
    top:35vh
  }

  .date {
    right: 38vw;
  }

  .days {
    right: 50vw;
  }

  .treatment {
    right: 62vw;
  }
  .open{
    width: 70vw;
    height: 8vh;
    position: fixed;
    top: 34vh;
    right: 15vw;
  }
  </style>