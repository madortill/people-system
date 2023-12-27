<template>
    <div id="app">
        <about></about>
        <openScreen v-if="numPage===1" @nextPage="changePage"></openScreen>
        <mainScreen v-if="numPage===2"></mainScreen>
    </div>
</template>

<script>
import About from './components/About.vue'
import MainScreen from './components/MainScreen.vue'
import OpenScreen from './components/OpenScreen.vue'
export default {
  components: {About, OpenScreen, MainScreen},
  data() {
    return {
        numPage: 1
    }
  },
  mounted () {


  },
  methods: {
    changePage() {
            this.numPage +=1;
        },
  }
}
</script>

<style >
body {
  margin: 0;
  overflow: hidden;
}
#app {
    direction: rtl;
}
</style>
