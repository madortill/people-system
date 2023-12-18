<template>
    <div id="openScreen">
        <!-- <img class="iconAbout" src="@/assets/media/aboutIcon.svg" @click="showAbout"> -->
        <div>ברוכים הבאים ללומדת מערכת אנשים <br>
            jfhgjfgjyhg jhjgjh jhjh hjhbgmj <br>
            dfdkmkgffghjbftghbtrfhngfdkmgkrthuit
        </div>
        <button @click="start"> בואו נתחיל </button>
    </div>
</template>

<script>
export default {
  data() {
    return {
    }
  },
  mounted () {


  },
  methods: {
    start() {

    },
    showAbout() {
        this.$emit("showAbout");
    }
  }
}
</script>

<style scoped>

</style>
