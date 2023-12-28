<template>
    <div id="openScreen">
        <div class="container">
            <!-- <div class="text">ברוכים הבאים ללומדת מערכת אנשים <br>
            jfhgjfgjyhg jhjgjh jhjh hjhbgmj <br>
            dfdkmkgffghjbftghbtrfhngfdkmgkrthuit
            </div> -->
            <button @click="start()" class="beginButton">התחל</button>
        </div>
    </div>
</template>

<script>
  export default {
    name: "openScreen",
    data() {
      return {
      }
    },
    methods: {
        start() {
            this.$emit(`nextPage`);
        }
    },
    computed: {
  
    }
  }
  </script>

<style scoped>
@font-face {
    font-family: "open";
    src: url("@/assets/Open_Sans (1)/OpenSans-VariableFont_wdth,wght.ttf");
  } 

#openScreen {
    display: flex;
    flex-direction: column;
    background-image: url('@/assets/Media/beginBackground.svg');
    background-repeat: no-repeat;
    background-size: cover;
    height: 100vh;
}

.beginButton {
    width: 10vw;
    height: 5vh;
    font-size: 1.5rem;
    position: fixed;
    font-family: "open";
    bottom: 10vh;
    box-shadow: 7px 23px 15px -3px rgba(0,0,0,0.1);
}

.container {
height: 15vh;
margin-top: 35vh;
display: flex;
flex-direction: column;
flex-wrap: nowrap;
justify-content: center;
align-items: center;
}
/* .text {
    font-size: 2vh;
    width: 20vw;
    height: 25vh;
    text-align: center;
} */

button {
    width: 5vw;
    height: 3vh;
    cursor: pointer;
}

</style>
