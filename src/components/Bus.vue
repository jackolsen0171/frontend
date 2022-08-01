<template>
  <div class="bus">
    <div class="bus-overlay border-blue-shadow"><div>Bus Times 🚌</div>
    </div>
    <div class="bus-overlay2">

       <div style="position: relative;left: 0.5vw" class="top-layer">
         <div class="location">
           <div class="location1">Location:</div>
           <div class="location2">The Three Hammers</div>
           <span style="font-size: 3vh;position: absolute;top: -0.9vh;left: 7vw;">˃</span>
           </div>
         <div class="bus-time">
           <div class="mins"><i>(Mins)</i></div>
           <div class="time1">{{polledData.edgware[0]}}</div>
           <div class="time2">{{polledData.edgware[1]}}</div>
         </div>
         <div class="bus-times"></div>
         <div class="destination">
           <div style="position: relative;right: 5.5vw;bottom: 8.5vh;" class="destination1">Destination:</div>
           <div style="position: relative;right: 5.5vw;bottom: 8.5vh" class="destination2">Edgware</div>
           <span style="font-size: 3vh;position: absolute;bottom: 2.5vh;left: 8vw;">˃</span></div>
       </div>

       <div style="position: relative;left: 5vw" class="bus-arrow">
            <div class="start-point"></div>
            <div class="arrow">
            </div>
            <div class="end-point"></div>
       </div>
    </div>
    <div class="bus-overlay3">
      <div  style="position:relative;left: 2vw"  class="top-layer">
        <div class="location">
          <div class="location1">Location:</div>
          <div class="location2">Belmont Farm</div>
          <span style="font-size: 3vh;position: absolute;top: -0.8vh;left: 4.5vw;">˃</span>
        </div>
        <div class="bus-time">
          <div class="mins"><i>(Mins)</i></div>
          <div class="time1">{{polledData.golders[0]}}</div>
          <div class="time2">{{polledData.golders[1]}}</div>
        </div>
        <div class="bus-times"></div>
        <div class="destination">
          <div style="position: relative;bottom: 8.5vh;" class="destination1">Destination:</div>
          <div style="position: relative;bottom: 8.5vh;width: 9vw" class="destination2">Golders Green</div>
          <span style="font-size: 3vh;position: absolute;bottom: 2.5vh;left: 5.8vw;">˃</span></div>
      </div>
      <div style="position: relative;top: -20vh" class="bus-arrow">
        <div class="start-point"></div>
        <div class="arrow">
        </div>
        <div class="end-point"></div>
      </div>
    </div>
<!--    <div class="bus-overlay4 border-blue"></div>-->
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'HelloWorld',
  data() {
    return {
      polling: null,
      polledData: {
        edgware: ['loading..', 'loading..'],
        golders: ['loading..', 'loading..'],
      },
      polledDate: "loading timestamp..."
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const bus = (await (await fetch('https://fathomless-crag-41517.herokuapp.com/bus')).json());
        // this.polledData = bus
        this.polledData = {
          edgware: [
              bus.edgware[0] || "N/A",
              bus.edgware[1] || ""
          ],
          golders: [
            bus.golders[0] || "N/A",
            bus.golders[1] || ""
          ]
        }
      }, 40000)
    },
    pullData() {
      axios
          .get('https://fathomless-crag-41517.herokuapp.com/bus')
          .then(response => (this.polledData = {
            edgware: [
              response.data.edgware[0] || "N/A",
              response.data.edgware[1] || ""
            ],
            golders: [
              response.data.golders[0] || "N/A",
              response.data.golders[1] || ""
            ]
          }))
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.border-blue{
  /*box-shadow: 0.2vh 0.2vh 2.5vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;
  /*box-shadow: 0.2vh 0.2vh 0.3vh 0.6vh #7dc5ef,  0.2vh 0.2vh 0.7vh 0.6vh #4587e4,  0.2vh 0.2vh 1vh 0.6vh #0861ef*/

}

.border-blue-shadow{
  box-shadow: 0.2vh 0.2vh 0.1vh 0.2vh #1d94d9, 0.5vh 0.3vh 0.1vh 0.4vh #4c2bed, 0vh 0vh 3vh 2vh #1e1d1d;

}

.bus {
  grid-column: 1/12;
  grid-row:17/31;
  background: #2a2828;
  color: white;
  display: grid;
  grid-template-rows: repeat(16, 1fr);
  grid-template-columns: repeat(16, 1fr);
  overflow: hidden;
  font-family: "Poppins", sans-serif;

}

.bus-overlay{
  background: #2a2828;
  grid-row: 1/4;
  grid-column: 1/12;
  position: relative;
  right: 5vw;
  border-bottom-right-radius: 2vh;
  border-bottom-left-radius: 2vh;
  font-size: 4vh;
  padding-left: 3vw;
  padding-top: 0.5vh;
  font-weight: 500;

}

.bus-overlay div{
  position: relative;
  left: 3.5vw;
}


.bus-overlay2{
  background: #2a2828;
  grid-row: 6/17;
  grid-column: 4/8;
  position: relative;
  bottom: 1.3vh;
}

.top-layer{
  height: 20vh;
}

.location1{
  position: relative;
  right: 6.5vw;
  opacity: 0.8;
  font-size: 1.5vh;
  font-weight: 600;
}

.location2{
  position: relative;
  right: 6.5vw;
  font-size: 2.3vh;
  font-weight: 500;
  width: 14vw;
}
.destination{
  position: relative;
  top: 8vh;
  padding-left: 0.3vw;
  right: 1.3vw;
}

.destination1{
  position: relative;
  top: -4vh;
  right: 5.5vw;
  opacity: 0.5;
  font-size: 1.5vh;
  font-weight: 600;

}

.destination2{
  position: relative;
  top: -3.5vh;
  right: 5.5vw;
  font-size: 1.8vh;
  font-weight: 500;
}


.bus-arrow{
  display: flex;
  flex-direction: column;
  align-items:center;
  position: relative;
  left: 4vw;
  bottom: 20vh;
}


.start-point{
  border-radius: 50%;
  width: 1vw;
  height: 1.8vh;
  background-color: white;
  box-shadow:inset  0vh 0vh 0.1vh 0.3vh #1590f1, 0vh 0vh 0.1vh 0.2vh #4c2bed;
  /*position: relative;*/
  /*left: 1vw;*/
  /*top: 1.8vh;*/


}
.arrow{
  background: white;
  width: 0.5vw;
  height: 21vh;
  border-radius: 2vh;
  box-shadow: inset 0.1vh 0.1vh 0.3vh 0.1vh #626365;


}
.end-point{
  border-radius: 50%;
  width: 1vw;
  height: 1.8vh;
  background-color: white;
  box-shadow:inset  0vh 0vh 0.1vh 0.3vh #1590f1, 0vh 0vh 0.1vh 0.2vh #4c2bed;
  /*position: relative;*/
  /*left: 15vw;*/
}

.bus-time{
  height: 10vh;
  position: relative;
  right: 2.5vw;

}
.mins{
  position: relative;
  left: 2.5vw;
  top: 1vh;
  font-weight: 700;
  opacity: 0.5;

}

.time1{
  font-size: 8vh;
  position: relative;
  bottom: 1vh;
  right: 4vw;

}
.time2{
  font-size: 3vh;
  position: relative;
  left: 3vw;
  bottom: 7.5vh;
  opacity: 0.5;
}


.bus-overlay3{
  background: #2a2828;
  grid-row: 6/17;
  grid-column: 12/16;
  position: relative;
  bottom: 1.3vh;
}
.bus-overlay4{
  background: #2a2828;
  grid-row: 15/19;
  grid-column: 1/19;
  border-radius: 5vh;
  z-index: 2;
  display: flex;
  flex-direction: column;
  position: relative;
  top: 2vh;

}

.bus-overlay4 img{
  width: 7vw;
  height: 10vh;
}




</style>
