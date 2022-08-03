<template>
  <div class="weather">
      <div class="title">Mill Hill Weather&nbsp;<ion-icon style="position: relative;top: 0.5vh" name="cloudy-night-outline"></ion-icon></div>
      <div class="current-temp">{{ polledData.current.temp }}°C</div>
      <div class="current-desc">{{ polledData.current.desc }}</div>
    <div class="line-container">
      <div class="line"></div>
    </div>
    <div class="weather-overlay2">
      <div class="weather-data-container">
        <div class="w-data1">
          <p>{{ polledData.forecast[0].time }}:00</p>
          <h1>{{ polledData.forecast[0].temp }}°C</h1>
          <img :src="polledData.forecast[0].icon" class="weather-data-Icon">
          <h5 class="weather-data-desc">{{ polledData.forecast[0].desc }}</h5>

        </div>
        <div class="w-data2">
          <p>{{ polledData.forecast[1].time }}:00</p>
          <h1>{{ polledData.forecast[1].temp }}°C</h1>
          <img :src="polledData.forecast[1].icon" class="weather-data-Icon">
          <h5 class="weather-data-desc">{{ polledData.forecast[1].desc }}</h5>
        </div>
        <div class="w-data3">
          <p>{{ polledData.forecast[2].time }}:00</p>
          <h1>{{ polledData.forecast[2].temp }}°C</h1>
          <img :src="polledData.forecast[2].icon" class="weather-data-Icon">
          <h5 class="weather-data-desc">{{ polledData.forecast[2].desc }}</h5>
        </div>
      </div>
    </div>
    <div class="weather-overlay3"></div>
<!--        <div class="weather-overlay1">-->
<!--          <div class="weather-location">Mill Hill Weather-->
<!--          </div>-->
<!--          <div class="w-temperature">-->
<!--            <p><span style="position: relative;top: 1vh">{{ polledData.current.temp }}</span><sup-->
<!--                class="temp-blue" style='font-size: 2.5vh;position: relative;bottom: 1vh;font-weight: 600'>°C</sup></p>-->
<!--          </div>-->
<!--          <div class="feels-like-text">-->
<!--            <div>Feels Like:</div>-->
<!--          </div>-->
<!--          <div class="feels-like-value">{{ polledData.current.feelsLike }}<span class = 'temp-blue'>°</span>C</div>-->
<!--          <div class="w-wind-icon">-->
<!--            &lt;!&ndash;        <img src='../assets/wind1.png'>&ndash;&gt;-->
<!--            <img src='../assets/wind2.png'>-->
<!--          </div>-->
<!--          <div class="wind-speed">-->
<!--            <p><span style="font-weight: 600;">{{ polledData.wind.kmh }}</span><span> Km/Hr</span></p>-->
<!--          </div>-->
<!--          <div class="wind-speed">-->
<!--              <p>Wind Speed:</p>-->
<!--          </div>-->
<!--          <div class="wind-speed-value">{{ polledData.wind.kmh }}<span style="font-size: 1.5vh"> Km<span class="temp-blue">/</span>Hr</span></div>-->

<!--        </div>-->
<!--        <div class="weather-overlay2 border-blue-shadow">-->
<!--          <div class="sunrise">-->
<!--            <img src='../assets/iconmonstr-weather-107-240.png'>-->
<!--            <h4>{{ polledData.sunrise }}</h4>-->
<!--          </div>-->
<!--          <div class="sunset">-->
<!--            <img src='../assets/iconmonstr-weather-109-240.png'>-->
<!--            <h4>{{ polledData.sunset }}</h4>-->
<!--          </div>-->
<!--        </div>-->
<!--        <div class="weather-overlay3 border-blue">-->
<!--          &lt;!&ndash;      <img src='../assets/wave-haikei.png'>&ndash;&gt;-->
<!--          <div class="weather-data-container">-->
<!--            <div class="w-data1">-->
<!--              <p>{{ polledData.forecast[0].time }}</p>-->
<!--              <h1>{{ polledData.forecast[0].temp }}°C</h1>-->
<!--              <img :src="polledData.forecast[0].icon" class="weather-data-Icon">-->
<!--              <h5 class="weather-data-desc">{{ polledData.forecast[0].desc }}</h5>-->

<!--            </div>-->
<!--            <div class="w-data2">-->
<!--              <p>{{ polledData.forecast[1].time }}</p>-->
<!--              <h1>{{ polledData.forecast[1].temp }}°C</h1>-->
<!--              <img :src="polledData.forecast[1].icon" class="weather-data-Icon">-->
<!--              <h5 class="weather-data-desc">{{ polledData.forecast[1].desc }}</h5>-->
<!--            </div>-->
<!--            <div class="w-data3">-->
<!--              <p>{{ polledData.forecast[2].time }}</p>-->
<!--              <h1>{{ polledData.forecast[2].temp }}°C</h1>-->
<!--              <img :src="polledData.forecast[2].icon" class="weather-data-Icon">-->
<!--              <h5 class="weather-data-desc">{{ polledData.forecast[2].desc }}</h5>-->
<!--            </div>-->
<!--            <div class="w-data4">-->
<!--              <p>{{ polledData.forecast[3].time }}</p>-->
<!--              <h1>{{ polledData.forecast[3].temp }}°C</h1>-->
<!--              <img :src="polledData.forecast[3].icon" class="weather-data-Icon">-->
<!--              <h5 class="weather-data-desc">{{ polledData.forecast[3].desc }}</h5>-->
<!--            </div>-->
<!--            <div class="w-data5">-->
<!--              <p>{{ polledData.forecast[4].time }}</p>-->
<!--              <h1>{{ polledData.forecast[4].temp }}°C</h1>-->
<!--              <img :src="polledData.forecast[4].icon" class="weather-data-Icon">-->
<!--              <h5 class="weather-data-desc">{{ polledData.forecast[4].desc }}</h5>-->
<!--            </div>-->
<!--          </div>-->
<!--        </div>-->
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

.border{
  box-shadow: 0 0 0.1vh 0.6vh #FFB562, 0 0 0.1vh 1.2vh #3AB0FF;
}

.temp-blue{
  color: #2196f3
}
.temp-red {
  /*color: #ff7420;*/
}
.border-blue{
  /*box-shadow: 0.2vh 0.2vh 2.5vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  box-shadow: 0.2vh 0.2vh 0.1vh 0.2vh #1d94d9, 0.5vh 0.3vh 0.1vh 0.4vh #4c2bed;
  /*box-shadow: 0.2vh 0.2vh 0.3vh 0.6vh #7dc5ef,  0.2vh 0.2vh 0.7vh 0.6vh #4587e4,  0.2vh 0.2vh 1vh 0.6vh #0861ef*/
}
.border-red{
  box-shadow: 0.2vh 0.2vh 1vh 0.5vh #ff7420, 0.5vh 0.3vh 1vh 1vh #ed2b2b;
}
.border-blue-shadow{
  box-shadow: 0.2vh 0.2vh 0.1vh 0.2vh #1d94d9, 0.5vh 0.3vh 0.1vh 0.4vh #4c2bed, 0vh 0vh 3vh 2vh #1e1d1d;
  /*box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh turquoise, 0.5vh 0.3vh 0.1vh 1vh limegreen;*/
}


.weather {
  /*grid-column: 2/14;*/
  grid-row: 15/31;
  grid-column: 19/31;
  font-family: 'Poppins', sans-serif;
  overflow: hidden;
  border-left: 2px solid #e0d8d8;
  border-right: 2px solid #e0d8d8;
  border-radius: 2vh;
  display: grid;
  grid-template-rows: repeat(8,1fr);
  grid-template-columns: repeat(8,1fr);
}

.title{
  text-align: center;
  font-size: 4vh;
  font-weight: 300;
  grid-row: 1/2;
  grid-column: 1/9;
  position: relative;
  top: 2vh;
  /*border: 2px solid red;*/

}



.current-temp{
  font-size: 7vh;
  font-weight: 600;
  grid-row: 2/3;
  grid-column: 1/9;
  text-align: center;
  position: relative;
  top: 1vh;
}

.current-desc{
  font-weight: 600;
  grid-row: 3/4;
  grid-column: 1/9;
  text-align: center;
  position: relative;
  top: 0vh;
}

.line-container{
  display: flex;
  justify-content: center;
  align-items: center;
  grid-row: 3/4;
  grid-column: 1/9;
  position: relative;
  top: 2.5vh;

}

.line{
  border: 1px solid rgba(0,0,0,1);
  width: 22vw;
  height: 1px;
  opacity: 0.8;
  border-radius: 50%;

}


.weather-overlay2{
  grid-column: 1/10;
  grid-row: 6/11;
  border-radius: 2vh;
  /*border: 2px solid red;*/
}

.weather-data-container{
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  position: relative;
  bottom: 9vh;
  /*border: 2px solid red;*/
}
.weather-data-container div {
  /*border: 2px solid red;*/
}
.weather-data-container p {
  text-align: center;
  color: black;
  /*font-weight: bold;*/
  font-size: 2.5vh;
  /*border: 2px solid red;*/
}
.weather-data-container h1 {
  text-align: center;
  color: black;
  border: 0.2vh solid black;
  border-radius: 2vh;
  margin-top: 1vh;
  font-size: 3.5vh;
}
.weather-data-Icon {
  width: 5vw;
  height: 8vh;
  margin-top: 1vh;
  border-bottom: 0.1vh solid black;
}
.weather-data-container h5 {
  text-align: center;
  color: black;
  padding-top: 0.5vh;
  font-size: 1.5vh;
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