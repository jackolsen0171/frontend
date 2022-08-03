<template>
  <div class="side-bar">
<!--    <div class="img-container"><img src="@/assets/Mill_Hill_School_Coat_of_Arms_(2017).png"></div>-->
    <div class="department-name">Physics&nbsp;🔭</div>
    <div class="desc">information dashboard</div>
    <hr style="border: 1px solid rgba(0,0,0,0.6);position: relative;left: 1.5vw;bottom:1.5vh;width: 20.5vw">
    <div class="side-bar-period">
      <p style="width: 10vw">Period 4<span>12:10 → 12:50</span></p>
      <div class="period-squares">
        <div></div>
        <div></div>
        <div></div>
        <div style="background-color: #F87474;"></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
      </div>

    </div>
<!--    <i class="et-virtutem">et virtutem et musas</i>-->
    <div class="side-bar-overlay">
      <div class="widget-rotation">
             <ul>
               <li style="opacity: 0.5"><ion-icon name="alert-outline"></ion-icon>&nbsp;&nbsp;&nbsp;MHS Notices</li>
               <li><span><ion-icon  name="cloudy-night-outline"></ion-icon></span>&nbsp;&nbsp;&nbsp;weather</li>
               <li style="opacity: 0.5"><ion-icon name="car-outline"></ion-icon>&nbsp;&nbsp;&nbsp;Bus</li>
               <li style="opacity: 0.5"><ion-icon name="videocam-outline"></ion-icon>&nbsp;&nbsp;&nbsp;School Video</li>
             </ul>
      </div>


    </div>
  </div>
  
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

/*hr {*/
/*  border: 0;*/
/*  clear:both;*/
/*  display:block;*/
/*  width: 70%;*/
/*  position: relative;*/
/*  left: 1vw;*/
/*  bottom: 0vh;*/
/*  background-color: #c3bfbf;*/
/*  height: 1px;*/
/*}*/


.side-bar{
  overflow: hidden;
  display: flex;
  flex-direction: column;
  background: white;
  border: 2px solid #e0d8d8;



}



.department-name{
  font-family: "Poppins", sans-serif;
  font-size: 8vh;
  color: black;
  font-weight: 600;
  padding: 3vh;
  width: 30vw;

}


.desc{
  font-size: 2.5vh;
  display: block;
  width: 30vw;
  font-family: "Poppins", sans-serif;
  font-weight: 500;
  position: relative;
  left: 1.75vw;
  bottom: 2vh;
  opacity: 0.8;
}

.side-bar-period{
  font-weight: 500;
  padding: 0 0 0 3vh;
  font-size: 3vh;
  position: relative;
  top: 3vh;
  font-family: "Poppins", sans-serif;
  display: flex;
  flex-direction: row;
  /*color: #F87474;*/
}

.side-bar-period p span{
  position: absolute;
  left: 12vw;
  font-size: 3vh;
}

.period-squares{
  display: flex;
  flex-direction: row;
  position: absolute;
  top: 8vh;
  justify-content: space-around;
  width: 20.5vw;
  height: 5vh;
}

.period-squares > div{
  background-color: #F9F2ED;
  border: 2px solid #e0d8d8;
  border-radius: 0.5vh;
  width: 2vw;
  height: 3.5vh;

}









.side-bar-overlay {
  background: white;
  border-radius: 7vh;
  position: relative;
  top:18vh;
  right: 0.15vw;
  height:100vh;
  width: 25vw;
  box-shadow: 0 0 0.1vh 0.6vh #FFB562, 0 0 0.1vh 1.2vh #3AB0FF;
  display: flex;
  justify-content: center;
  align-content: center;
}

.widget-rotation{
  /*margin: auto;*/
  position: relative;
  top: 6vh;
  left: 2vw;
  height: 35vh;
  width: 25vw;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  border-radius: 2vh;
  background: #ffffff;
  /*box-shadow: inset 0.1vh 0.1vh 1vh #a098a9,inset -0.1vh -0.1vh 1vh #a098a9;*/
}

.widget-rotation ul{
  font-family: "Poppins", sans-serif;
  width: 20vw;
  height: 40vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-content:center;

}
.widget-rotation ul li{
  list-style: none;
  height: 7vh;
  font-size: 2.8vh;
  display: flex;
  justify-content: start;
  align-items: center;
  width: 15vw;
  padding-left: 1vw;
  font-weight: 500;
}

.widget-rotation ul li:nth-child(2){
  border-radius: 10vh;
  background-color: #F9F2ED;
  border: 4px solid #e0d8d8;
  box-shadow: 0.1vh 0.1vh 1vh 1vh #fbf8f5;
}

.widget-rotation ul li span{
  padding-top: 0.5vh;
  color: #F87474;
}









</style>