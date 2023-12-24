<template>
    <div id="openScreen">
        <div class="container">
            <div class="text">ברוכים הבאים ללומדת מערכת אנשים <br>
            jfhgjfgjyhg jhjgjh jhjh hjhbgmj <br>
            dfdkmkgffghjbftghbtrfhngfdkmgkrthuit
            </div>
            <button @click="start()">התחל</button>
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
#openScreen {
    display: flex;
    flex-direction: column;
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
.text {
    font-size: 2vh;
    width: 20vw;
    height: 25vh;
    text-align: center;
}

button {
    width: 5vw;
    height: 3vh;
}

</style>
