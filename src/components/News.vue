<template>
  <div class="news">
      <div class="triangle1"></div>
      <div class="triangle2"></div>
      <div class="triangle3"></div>
      <div class="title">Daily News&nbsp;<ion-icon style="position: relative;top: 0.5vh" name="newspaper-outline"></ion-icon></div>
      <div class="headline">{{ polledData[startNum].title }}</div>
      <div class="news-data">{{ polledData[startNum].description }}</div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Department-notices",
  data() {
    return {
      polling: null,
      startNum: 0,
      polledData: ['loading...', 'loading...', 'loading...'],
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const news = (await (await fetch('https://mhs-backend.herokuapp.com/news-db')).json());
        this.polledData = news
        this.startNum >= this.polledData.length ? this.startNum = 0 : this.startNum+=1
      }, 10000)
    },
    pullData() {
      axios
          .get('https://mhs-backend.herokuapp.com/news-db')
          .then(response => (this.polledData = response.data))
    }
  },
  mounted() {
    this.pullData()
  },
  beforeDestroy() {
    clearInterval(this.polling)
  },
  created() {
    this.pollData()

  }
}
</script>

<style scoped>




.news {
  grid-row: 15/31;
  grid-column: 2/17;
  overflow: hidden;
  font-family: "Poppins", sans-serif;
  padding: 2vh;
  border-radius: 2vh;
  display: grid;
  grid-template-columns: repeat(15, 1fr);
  grid-template-rows: repeat(15, 1fr);
  border-left: var(--borderWidth) solid var(--color5);
  border-right: var(--borderWidth) solid var(--color5);

}

.title{
  font-size: 4vh;
  grid-row: 1/3;
  grid-column: 1/10;
  font-weight: 300;
}

.headline{
  grid-row: 4/8;
  grid-column: 1/15;
  font-weight: 200;
  font-size: 4vh;

}

.news-data{
  grid-row: 9/16;
  grid-column: 1/16;
  font-size: 2vh;
  font-weight: 100;
}

.triangle1 {
  width: 0;
  height: 0;
  border-left: 1.25vh solid transparent;
  border-right: 1.25vh solid transparent;
  border-bottom: 2vh solid var(--color3);
  grid-row: 1/2;
  grid-column: 15/16;
  transform: rotate(70deg);
  filter: blur(0.1vh);
}

/*.triangle2 {*/
/*  width: 0;*/
/*  height: 0;*/
/*  border-left: 1vh solid transparent;*/
/*  border-right: 1vh solid transparent;*/
/*  border-bottom: 2vh solid var(--color3);*/
/*  !*position: relative;*!*/
/*  !*right: 20vw;*!*/
/*  !*top: 32vh;*!*/
/*  grid-row: 16/16;*/
/*  grid-column: 1/2;*/
/*  transform: rotate(220deg);*/
/*  filter: blur(0.1vh);*/
/*}*/

.triangle3 {
  width: 0;
  height: 0;
  border-left: 0.75vh solid transparent;
  border-right: 0.75vh solid transparent;
  border-bottom: 2vh solid var(--color3);
  grid-row: 14/15;
  grid-column: 15/16;
  transform: rotate(30deg);
  filter: blur(0.1vh);
}
</style>