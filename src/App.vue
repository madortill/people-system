<template>
    <div id="app">
        <!-- <img class="iconAbout" src="@/assets/media/aboutIcon.svg" @click="showAbout"> -->
        <about v-if="showAbout"></about>
        <openScreen @showAbout="showAbout"></openScreen>
    </div>
</template>

<script>
import About from './components/About.vue'
import OpenScreen from './components/OpenScreen.vue'
export default {
  components: {About, OpenScreen},
  data() {
    return {
        showAbout: false,
    }
  },
  mounted () {


  },
  methods: {
    showAbout() {
        this.showAbout = true
    }
  }
}
</script>

<style scoped>
#app {
    direction: rtl;
}

.iconAbout {
    width:5vw;
    height: 5vh;
    position: fixed;
    margin-top: 1vh;
    margin-left: 95vw;
  }
</style>
