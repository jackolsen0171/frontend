<template>
  <div class="weather">

     <div class="top-bar">
       <div class="title">Mill Hill Weather&nbsp;<ion-icon style="position: relative;top: 0.5vh" name="cloudy-night-outline"></ion-icon></div>


     </div>
    <div class="line"></div>
    <div class="weather-overlay2">
      <div class="weather-data-container">
        <div class="w-data1">
          <p>Now</p>
          <h1>{{ polledData.forecast[0].temp }}<span style="color: var(--color3)">°</span>C</h1>
          <img :src="polledData.forecast[0].icon" class="weather-data-Icon">
          <h5 class="weather-data-desc">{{ polledData.forecast[0].desc }}</h5>

        </div>
        <div class="w-data2">
          <p>{{ polledData.forecast[1].time }}<span style="color: var(--color3)">:</span>00</p>
          <h1>{{ polledData.forecast[1].temp }}<span style="color: var(--color3)">°</span>C</h1>
          <img :src="polledData.forecast[1].icon" class="weather-data-Icon">
          <h5 class="weather-data-desc">{{ polledData.forecast[1].desc }}</h5>
        </div>
        <div class="w-data3">
          <p>{{ polledData.forecast[2].time }}<span style="color: var(--color3)">:</span>00</p>
          <h1>{{ polledData.forecast[2].temp }}<span style="color: var(--color3)">°</span>C</h1>
          <img :src="polledData.forecast[2].icon" class="weather-data-Icon">
          <h5 class="weather-data-desc">{{ polledData.forecast[2].desc }}</h5>
        </div>
      </div>
    </div>


  </div>

</template>

<script>

import axios from "axios";

export default {
  name: "Weather",
  data() {
    return {
      tempThresh: 3,
      polling: null,
      polledData: {
        "hour": "22/24",
        "wind": {
          "ms": 2.06,
          "kmh": 7
        },
        "sunrise": "05:26",
        "sunset": "20:47",
        "current": {
          "temp": 21,
          "feelsLike": 21,
          "desc": "few clouds",
          "icon": "http://openweathermap.org/img/wn/02n@2x.png",
          "humidity": 77
        },
        "forecast": [
          {
            "time": "01",
            "temp": 20,
            "desc": "few clouds",
            "icon": "http://openweathermap.org/img/wn/02n@2x.png"
          },
          {
            "time": "04",
            "temp": 17,
            "desc": "broken clouds",
            "icon": "http://openweathermap.org/img/wn/04n@2x.png"
          },
          {
            "time": "07",
            "temp": 15,
            "desc": "broken clouds",
            "icon": "http://openweathermap.org/img/wn/04d@2x.png"
          },
          {
            "time": "10",
            "temp": 20,
            "desc": "broken clouds",
            "icon": "http://openweathermap.org/img/wn/04d@2x.png"
          },
          {
            "time": "13",
            "temp": 23,
            "desc": "broken clouds",
            "icon": "http://openweathermap.org/img/wn/04d@2x.png"
          },
          {
            "time": "16",
            "temp": 24,
            "desc": "overcast clouds",
            "icon": "http://openweathermap.org/img/wn/04d@2x.png"
          },
          {
            "time": "19",
            "temp": 22,
            "desc": "overcast clouds",
            "icon": "http://openweathermap.org/img/wn/04d@2x.png"
          }
        ]

      }
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const weather = (await (await fetch('https://mhs-backend.herokuapp.com/weather3')).json());
        this.polledData = weather


      }, 60000)
    }, pullData() {
      axios
          .get('https://mhs-backend.herokuapp.com/weather3')
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


.weather {
  grid-row: 1/15;
  grid-column: 2/17;
  font-family: 'Poppins', sans-serif;
  overflow: hidden;
  border-radius: 2vh;
  display: grid;
  grid-template-rows: repeat(8,1fr);
  grid-template-columns: repeat(8,1fr);
  border-left: var(--borderWidth) solid var(--color5);
  border-right: var(--borderWidth) solid var(--color5);
}

.top-bar{
  grid-row: 1/4;
  grid-column: 1/9;
}

.title{
  padding: 2vh;
  font-size: 5vh;
  font-weight: 300;
  text-align: center;
  /*border: 2px solid red;*/

}


.weather-overlay2{
  grid-column: 1/10;
  grid-row: 6/11;
  border-radius: 2vh;
  position: relative;
  bottom: 3vh;
}

.weather-data-container{
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  position: relative;
  bottom: 9vh;
}

.weather-data-container p {
  text-align: center;
  font-size: 3vh;
}
.weather-data-container h1 {
  text-align: center;
  border: var(--borderWidth) solid var(--color4);
  border-radius: 2vh;
  margin-top: 1vh;
  padding: 0.5vh;
  font-weight: 300;
}
.weather-data-Icon {
  width: 5vw;
  height: 8vh;
  margin-top: 1vh;
  border-radius: 1vh;
  border-bottom: var(--borderWidth) solid var(--color4);
}
.weather-data-container h5 {
  text-align: center;
  padding-top: 0.5vh;
  font-size: 1.5vh;
  font-weight: 300;
}
.weather-icon {
  grid-row: 2/5;
  grid-column: 2/5;
}
.weather-icon img {
  width: 5vw;
  height: 6vh;
}
.weather-location {
  grid-row: 3/8;
  grid-column: 2/16;
  font-size: 2.7vh;
  /*border: 2px solid red;*/
}
.w-temperature {
  grid-row: 7/16;
  grid-column: 2/6;
  font-size: 8vh;
}
.w-temperature p {
  position: relative;
  bottom: 2vh;
}
.w-degrees {
  grid-row: 9/11;
  grid-column: 6/7;
  position: relative;
  right: 0.7vw;
  bottom: 1vh;
}
.feels-like-text {
  grid-row: 9/14;
  grid-column: 9/13;
  border-bottom: 0.2vh solid white;
  font-size: 1.5vh;
  font-weight: 500;
  position: relative;
  right: 0.5vw;
}
.feels-like-text div {
  position: relative;
  top: 0.8vh;
  width: 10vw;
}
.feels-like-value {
  grid-row: 14/18;
  grid-column: 9/13;
  font-size: 2.5vh;
  position: relative;
  right: 0.5vw;
}
.wind-speed{
  grid-row: 9/14;
  grid-column: 15/20;
  border-bottom: 0.2vh solid white;
  font-size: 1.5vh;
  font-weight: 400;
  position: relative;
  right: 0.5vw;
}
.wind-speed p{
  position: relative;
  top: 0.8vh;
  width: 10vw;
}
/*.wind-speed-value{*/
/*  grid-row: 14/18;*/
/*  grid-column: 15/20;*/
/*  font-size: 2.5vh;*/
/*  position: relative;*/
/*  right: 0.5vw;*/
/*}*/
/*.w-wind-icon img{*/
/*  position: absolute;*/
/*  width: 5vw;*/
/*  height: 7vh;*/
/*  left: 15vw;*/
/*}*/

</style>