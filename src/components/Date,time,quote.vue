<template>
  <div class="DateTime">
    <div class="time-main">
      <div>{{ localHr }}<span style="color: var(--color3)">:</span>{{ mins }}<span style="color: var(--color3)" >:</span>{{ secs }}</div>
    </div>
    <div class="date-main">
      <div>{{ day }} {{ date }} {{ month }}</div>
    </div>
<!--    <img src="@/assets/Mill_Hill_School_Coat_of_Arms_(2017).png">-->
    <em class="motto">
      <div>et virtutem et musas</div>
    </em>
    <em class="motto-translation">instilling values, inspiring minds.</em>
  </div>
<!--    <div class="date-overlay1 border-blue-shadow">-->
<!--      <h1>{{ localHr }}:{{ mins }}:{{ secs }}</h1>-->
<!--      <div class="date-line1"></div>-->
<!--      <h2>{{ day }} {{ date }} {{ month }}</h2>-->
<!--      <div class="date-clock-icon">-->

<!--      </div>-->

<!--    </div>-->
<!--    <div class="date-overlay2">-->
<!--      <div class="quote-container">-->
<!--        <div>Daily Quote 📔</div>-->
<!--        <i class="quote-text">{{quote}}</i>-->
<!--      </div>-->
<!--    </div>-->
<!--    <div class="date-overlay3 border-blue">-->
<!--      <div style="position: absolute;top: 1vh; opacity: 0.2;filter: blur(0.3vh); left: 3vw;width: 4vw;height: 6vh"-->
<!--           class="ellipse"></div>-->
<!--      <div style="position: absolute;top: 20vh; opacity: 0.2;filter: blur(0.3vh); left: 10vw;width: 6vw;height: 9vh"-->
<!--           class="ellipse"></div>-->
<!--      <div class="int-times">-->
<!--        <div><span class="nyc">NYC</span> {{ nycHr }}:{{ mins }} </div>-->
<!--        <div><span class="syd">SYD</span> {{ sydHr }}:{{ mins }} </div>-->
<!--        <div><span class="tky">TKY</span> {{ tokHr }}:{{ mins }} </div>-->
<!--      </div>-->
<!--    </div>-->


  <!--      <div class="int-times">-->
  <!--          <div><span class="nyc">NYC</span>  00:00:00 🗽</div>-->
  <!--          <div><span class="syd">SYD</span>  00:00:00 🦘</div>-->
  <!--          <div><span class="jpn">JPN</span>  00:00:00 🗾</div>-->
  <!--      </div>-->
  <!--     <div class="room-title">-->
  <!--        <h1>Room Uses 🗓</h1>-->
  <!--      </div>-->
  <!--        <div class="room-box">-->
  <!--          <div class="room-container1">-->
  <!--            <h1>IT 1:</h1>-->
  <!--            <h1>...</h1>-->
  <!--          </div>-->
  <!--          <div class="room-container2">-->
  <!--            <h1>IT 2:</h1>-->
  <!--            <h1>...</h1>-->
  <!--          </div>-->
  <!--          <div class="room-container3">-->
  <!--            <h1>IT 3:</h1>-->
  <!--            <h1>...</h1>-->
  <!--          </div>-->
  <!--          <div class="room-container4">-->
  <!--            <h1>IT 4:</h1>-->
  <!--            <h1>...</h1>-->
  <!--          </div>-->
  <!--        </div>-->


  <!--     <div class="quote">-->
  <!--       <div>Daily Quote </div>-->
  <!--       <i>filler text filler text here is some more filler text</i>-->
  <!--     </div>-->

  <!--    </div>-->
  <!--    <div class="date-overlay3"></div>-->
  <!--    <div class="date-overlay4">-->
  <!--      <div class="int-times">-->
  <!--        <div>NYC: 00:00:00 🇺🇸</div>-->
  <!--        <div>SYD: 00:00:00 🇦🇺</div>-->
  <!--        <div>JPN: 00:00:00 🇯🇵</div>-->
  <!--      </div>-->


  <!--    <div class="date-overlay5 border-blue">-->
  <!--      <div class="date-ellipse1"></div>-->
  <!--&lt;!&ndash;      <quote></quote>&ndash;&gt;-->
  <!--    </div>-->

</template>

<script>
// import quote from "@/components/Quote";

import axios from "axios";

export default {
  name: "Date-time",
  components: {
    // quote
  },
  data() {
    return {
      days: ["SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT"],
      months: ["JAN", "FEB", "MAR", "APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"],
      polling: null,
      localHr: "00",
      nycHr: "00",
      sydHr: "00",
      tokHr: "00",
      mins: "00",
      secs: "00",
      day: "day...",
      date: "number...",
      month: "month...",
      quote: {
        text: 'Text...',
      }
    }
  },
  methods:
      {
        pollData() {
          this.polling = setInterval(() => {
            const date = new Date()
            this.nycHr = date.toLocaleTimeString('en-GB', {timeZone: 'America/New_York'}).split(':')[0].padStart(2, '0')
            this.sydHr = date.toLocaleTimeString('en-GB', {timeZone: 'Australia/Sydney'}).split(':')[0].padStart(2, '0')
            this.tokHr = date.toLocaleTimeString('en-GB', {timeZone: 'Asia/Tokyo'}).split(':')[0].padStart(2, '0')
            //hours
            this.localHr = date.getHours().toString().padStart(2, '0')
            this.mins = date.getMinutes().toString().padStart(2, '0')
            this.secs = date.getSeconds().toString().padStart(2, '0')

            this.day = this.days[date.getDay()]
            this.date = date.getDate()
            this.month = this.months[date.getMonth()]
          }, 1000)
        },
        pullData() {
          axios
              .get('https://fathomless-crag-41517.herokuapp.com/quotes')
              .then(response => (this.quote = response.data[0].text))
        }
      },
  mounted() {
    this.pullData()
  },
  beforeDestroy() {
    clearInterval(this.polling)
  }
  ,
  created() {
    this.pollData()
  }
}
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Red+Hat+Mono&display=swap');


.DateTime {
  grid-column: 17/31;
  grid-row: 1/15;
  border-radius: 2vh;
  font-family: 'Poppins', sans-serif;
  border-left: var(--borderWidth) solid var(--color5);
  border-right: var(--borderWidth) solid var(--color5);
  /*background: var(--color2);*/

}



.time-main{
  font-size: 12vh;
  font-weight: 200;
  text-align: center;
  opacity: 0.9;
  letter-spacing: 0.5vh;
}

.date-main{
  font-size: 5vh;
  font-weight: 200;
  position: relative;
  bottom: 2vh;
  opacity: 0.8;
  text-align: center;
}

.motto{
  font-size: 3vh;
  font-weight: 100;
  opacity: 0.8;
  text-align: center;
  position: relative;
  bottom: 2vh;

}



.motto-translation{
  font-weight: 200;
  font-size: 4vh;
  display: block;
  text-align: center;
  position: relative;
  bottom: 2vh;


}


</style>