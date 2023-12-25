<template>
    <div id="app">
        <about></about>
        <openScreen v-if="numPage===1" @nextPage="changePage"></openScreen>
        <Main v-if="numPage===2"></Main>
    </div>
</template>

<script>
import About from './components/About.vue'
import Main from './components/Main.vue'
import OpenScreen from './components/OpenScreen.vue'
export default {
  components: {About, OpenScreen, Main},
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

<style scoped>
#app {
    direction: rtl;
}
</style>
