<template>
  <div class="news">
      <div class="triangle1"></div>
      <div class="triangle2"></div>
      <div class="triangle3"></div>
      <div class="title">Daily News&nbsp;<ion-icon style="position: relative;top: 0.5vh" name="newspaper-outline"></ion-icon></div>
      <div class="headline">Rishi Sunak vows to take 4p off income tax</div>
      <div class="news-data">Rishi Sunak has said he will cut the basic rate of income tax from 20% to 16% by the end of the next parliament if he becomes prime minister.</div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Department-notices",
  data() {
    return {
      days: ["SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT"],
      months: ["JAN", "FEB", "MAR", "APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"],
      day: "day...",
      date: "number...",
      month: "month...",
      polling: null,
      startNum: 0,
      polledData: ['loading...', 'loading...', 'loading...'],
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const news = (await (await fetch('https://fathomless-crag-41517.herokuapp.com/news-db')).json());
        this.polledData = news
        this.startNum >= this.polledData.length ? this.startNum = 0 : this.startNum+=1
      }, 10000)
    },
    pullData() {
      axios
          .get('https://fathomless-crag-41517.herokuapp.com/news-db')
          .then(response => (this.polledData = response.data))
    }
  },
  mounted() {
    this.pullData()
    const date = new Date()
    this.day = this.days[date.getDay()]
    this.date = date.getDate()
    this.month = this.months[date.getMonth()]
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
  grid-column: 14/31;
  grid-row: 1/14;
  overflow: hidden;
  color: black;
  font-family: "Poppins", sans-serif;
  border-right: 2px solid #e0d8d8;
  padding: 2vh;
  border-radius: 2vh;
  display: grid;
  grid-template-columns: repeat(15, 1fr);
  grid-template-rows: repeat(15, 1fr);
  border-left: 2px solid #e0d8d8;

}

.title{
  font-size: 4vh;
  grid-row: 1/3;
  grid-column: 1/10;
  font-weight: 300;
  position: relative;
  bottom: 2vh;
}

.headline{
  grid-row: 3/8;
  grid-column: 1/15;
  font-weight: 700;
  font-size: 4vh;
}

.news-data{
  grid-row: 9/16;
  grid-column: 1/16;
  font-size: 2.3vh;
}

.triangle1 {
  width: 0;
  height: 0;
  border-left: 1.25vh solid transparent;
  border-right: 1.25vh solid transparent;
  border-bottom: 2vh solid #3AB0FF;
  grid-row: 1/2;
  grid-column: 15/16;
  transform: rotate(70deg);
  filter: blur(0.1vh);
}

.triangle2 {
  width: 0;
  height: 0;
  border-left: 1vh solid transparent;
  border-right: 1vh solid transparent;
  border-bottom: 2vh solid #FFB562;
  /*position: relative;*/
  /*right: 20vw;*/
  /*top: 32vh;*/
  grid-row: 15/16;
  grid-column: 1/2;
  transform: rotate(220deg);
  filter: blur(0.1vh);
}

.triangle3 {
  width: 0;
  height: 0;
  border-left: 0.75vh solid transparent;
  border-right: 0.75vh solid transparent;
  border-bottom: 2vh solid #F87474;
  grid-row: 14/15;
  grid-column: 15/16;
  transform: rotate(30deg);
  filter: blur(0.1vh);
}
</style>