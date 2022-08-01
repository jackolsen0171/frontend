<template>
  <div class="weather">
<!--    <div class="weather-overlay1">-->
<!--      <div class="weather-location">Mill Hill Weather-->
<!--      </div>-->
<!--      <div class="w-temperature">-->
<!--        <p><span style="position: relative;top: 1vh">{{ polledData.current.temp }}</span><sup-->
<!--            class="temp-blue" style='font-size: 2.5vh;position: relative;bottom: 1vh;font-weight: 600'>°C</sup></p>-->
<!--      </div>-->
<!--      <div class="feels-like-text">-->
<!--        <div>Feels Like:</div>-->
<!--      </div>-->
<!--      <div class="feels-like-value">{{ polledData.current.feelsLike }}<span class = 'temp-blue'>°</span>C</div>-->
<!--      <div class="w-wind-icon">-->
<!--        &lt;!&ndash;        <img src='../assets/wind1.png'>&ndash;&gt;-->
<!--        <img src='../assets/wind2.png'>-->
<!--      </div>-->
<!--      <div class="wind-speed">-->
<!--        <p><span style="font-weight: 600;">{{ polledData.wind.kmh }}</span><span> Km/Hr</span></p>-->
<!--      </div>-->
<!--      <div class="wind-speed">-->
<!--          <p>Wind Speed:</p>-->
<!--      </div>-->
<!--      <div class="wind-speed-value">{{ polledData.wind.kmh }}<span style="font-size: 1.5vh"> Km<span class="temp-blue">/</span>Hr</span></div>-->

<!--    </div>-->
<!--    <div class="weather-overlay2 border-blue-shadow">-->
<!--      <div class="sunrise">-->
<!--        <img src='../assets/iconmonstr-weather-107-240.png'>-->
<!--        <h4>{{ polledData.sunrise }}</h4>-->
<!--      </div>-->
<!--      <div class="sunset">-->
<!--        <img src='../assets/iconmonstr-weather-109-240.png'>-->
<!--        <h4>{{ polledData.sunset }}</h4>-->
<!--      </div>-->
<!--    </div>-->
<!--    <div class="weather-overlay3 border-blue">-->
<!--      &lt;!&ndash;      <img src='../assets/wave-haikei.png'>&ndash;&gt;-->
<!--      <div class="weather-data-container">-->
<!--        <div class="w-data1">-->
<!--          <p>{{ polledData.forecast[0].time }}</p>-->
<!--          <h1>{{ polledData.forecast[0].temp }}°C</h1>-->
<!--          <img :src="polledData.forecast[0].icon" class="weather-data-Icon">-->
<!--          <h5 class="weather-data-desc">{{ polledData.forecast[0].desc }}</h5>-->

<!--        </div>-->
<!--        <div class="w-data2">-->
<!--          <p>{{ polledData.forecast[1].time }}</p>-->
<!--          <h1>{{ polledData.forecast[1].temp }}°C</h1>-->
<!--          <img :src="polledData.forecast[1].icon" class="weather-data-Icon">-->
<!--          <h5 class="weather-data-desc">{{ polledData.forecast[1].desc }}</h5>-->
<!--        </div>-->
<!--        <div class="w-data3">-->
<!--          <p>{{ polledData.forecast[2].time }}</p>-->
<!--          <h1>{{ polledData.forecast[2].temp }}°C</h1>-->
<!--          <img :src="polledData.forecast[2].icon" class="weather-data-Icon">-->
<!--          <h5 class="weather-data-desc">{{ polledData.forecast[2].desc }}</h5>-->
<!--        </div>-->
<!--        <div class="w-data4">-->
<!--          <p>{{ polledData.forecast[3].time }}</p>-->
<!--          <h1>{{ polledData.forecast[3].temp }}°C</h1>-->
<!--          <img :src="polledData.forecast[3].icon" class="weather-data-Icon">-->
<!--          <h5 class="weather-data-desc">{{ polledData.forecast[3].desc }}</h5>-->
<!--        </div>-->
<!--        <div class="w-data5">-->
<!--          <p>{{ polledData.forecast[4].time }}</p>-->
<!--          <h1>{{ polledData.forecast[4].temp }}°C</h1>-->
<!--          <img :src="polledData.forecast[4].icon" class="weather-data-Icon">-->
<!--          <h5 class="weather-data-desc">{{ polledData.forecast[4].desc }}</h5>-->
<!--        </div>-->
<!--      </div>-->
<!--    </div>-->
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
        "hour": "12/24",
        "wind": {
          "ms": 9.77,
          "kmh": 35
        },
        "sunrise": "07:01",
        "sunset": "17:27",
        "current": {
          "temp": 12,
          "feelsLike": 12
        },
        "forecast": [
          {
            "time": "15",
            "temp": 11,
            "desc": "light rain",
            "icon": "http://openweathermap.org/img/wn/10d@2x.png"
          },
          {
            "time": "18",
            "temp": 9,
            "desc": "broken clouds",
            "icon": "http://openweathermap.org/img/wn/04n@2x.png"
          },
          {
            "time": "21",
            "temp": 6,
            "desc": "clear sky",
            "icon": "http://openweathermap.org/img/wn/01n@2x.png"
          },
          {
            "time": "00",
            "temp": 5,
            "desc": "clear sky",
            "icon": "http://openweathermap.org/img/wn/01n@2x.png"
          },
          {
            "time": "03",
            "temp": 4,
            "desc": "clear sky",
            "icon": "http://openweathermap.org/img/wn/01n@2x.png"
          },

        ]
      }
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const weather = (await (await fetch('https://fathomless-crag-41517.herokuapp.com/weather3')).json());
        this.polledData = weather


      }, 60000)
    }, pullData() {
      axios
          .get('https://fathomless-crag-41517.herokuapp.com/weather3')
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
  grid-column: 15/29;
  grid-row: 18/24;
  font-family: 'Poppins', sans-serif;
  overflow: hidden;
  /*background-color: #F9F2ED;*/
  /*border: 2px solid #e0d8d8;*/
}

.weather-overlay1 {
  width: 35%;
  height: 100%;
  /*box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #f18f3f, 0.5vh 0.3vh 0.1vh 1vh #d71f56;*/
  border-top-right-radius: 2vh;
  border-bottom-right-radius: 2vh;
  z-index: 1;
  display: grid;
  grid-template-columns: repeat(20, 1fr);
  grid-template-rows: repeat(20, 1fr);
  /*box-shadow: 0 0 0.1vh 0.7vh #FFB562, 0 0 0.1vh 1.5vh #3AB0FF;*/

}

.weather-overlay2 {
  width: 11vw;
  background: #2a2828;
  height: 13vh;
  position: relative;
  bottom: 16vh;
  left: 23vw;
  /*box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  z-index: -1;
  border-bottom-right-radius: 2vh;
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(5, 1fr);
}

.sunrise {
  border-top-left-radius: 2vh;
  border-bottom-left-radius: 2vh;
  border-right: none;
  position: relative;
  left: 2vw;
  top: 1.5vh;
  width: 4.5vw;
  height: 8vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;

}

.sunrise img {
  width: 4vw;
  height: 6vh;
  position: relative;
  right: 1vw;
  top: 1.75vh;
}

.sunrise h4 {
  font-weight: 200;
  font-size: 2.5vh;
  position: relative;
  top: 2vh;
  right: 1vw;
}

.sunset {
  border-left: none;
  border-top-right-radius: 2vh;
  border-bottom-right-radius: 2vh;
  position: relative;
  top: 1.5vh;
  right: -2vw;
  width: 4.5vw;
  height: 8vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

.sunset img {
  width: 4vw;
  height: 6vh;
  position: relative;
  right: 0.5vw;
  top: 1.75vh;

}

.sunset h4 {
  font-weight: 200;
  font-size: 2.5vh;
  position: relative;
  top: 2vh;
  right: 0.5vw;
}





.weather-overlay3 {
  width: 100%;
  height: 80%;
  position: relative;
  bottom: 22vh;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-content: space-evenly;
  padding-top: 13vh;
  background: #2a2828;
  z-index: -2;
  border-bottom-left-radius: 2vh;
  border-bottom-right-radius: 2vh;
  border-top-right-radius: 2vh;
  /*box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/


}

.weather-overlay3 div {
  background-color: #2a2828;
  width: 10vw;
  height: 23vh;
  margin-left: 1vw;
  margin-right: 1vw;
  border-radius: 3vh;
  position: relative;
  bottom: 1vh;

}

.weather-data-container{
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  position: relative;
  right: 12.5vw;
  top: 0.5vh;
}

.weather-data-container div {

}


.weather-overlay3 p {
  text-align: center;
  color: white;
  font-weight: bold;
  font-size: 2.5vh;

}

.weather-overlay3 h1 {
  text-align: center;
  color: white;
  border: 0.2vh solid white;
  border-radius: 2vh;
  margin-top: 1vh;
  font-size: 3.5vh;

}

.weather-data-Icon {
  width: 5vw;
  height: 8vh;
  margin-top: 1vh;
  border-bottom: 0.1vh solid white;

}

.weather-overlay3 h5 {
  text-align: center;
  color: white;
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

.wind-speed-value{
  grid-row: 14/18;
  grid-column: 15/20;
  font-size: 2.5vh;
  position: relative;
  right: 0.5vw;
}

.w-wind-icon img{
  position: absolute;
  width: 5vw;
  height: 7vh;
  left: 15vw;
}






</style>