<template>
  <div class="side-bar">
<!--    <div class="img-container"><img src="@/assets/Mill_Hill_School_Coat_of_Arms_(2017).png"></div>-->
    <div class="department-name">Physics&nbsp;🔭</div>
    <div class="desc">information dashboard</div>
    <hr style="border: 1px solid rgba(0,0,0,0.6);position: relative;left: 1.5vw;bottom:1.5vh;width: 20.5vw">
    <div class="side-bar-period">
      <p style="width: 10vw">Period {{periodInfo.period}}<span>{{ periodInfo.lower }} → {{ periodInfo.upper }}</span></p>
      <div class="period-squares">
        <div :class="periodInfo.block==1 ? 'active-period' : 'inactive-period'"></div>
        <div :class="periodInfo.block==2 ? 'active-period' : 'inactive-period'"></div>
        <div :class="periodInfo.block==3 ? 'active-period' : 'inactive-period'"></div>
        <div :class="periodInfo.block==4 ? 'active-period' : 'inactive-period'"></div>
        <div :class="periodInfo.block==5 ? 'active-period' : 'inactive-period'"></div>
        <div :class="periodInfo.block==6 ? 'active-period' : 'inactive-period'"></div>
        <div :class="periodInfo.block==7 ? 'active-period' : 'inactive-period'"></div>
        <div :class="periodInfo.block==8 ? 'active-period' : 'inactive-period'"></div>
        <div :class="periodInfo.block==9 ? 'active-period' : 'inactive-period'"></div>
      </div>

    </div>
<!--    <i class="et-virtutem">et virtutem et musas</i>-->
    <div class="side-bar-overlay">
      <div class="widget-rotation">
             <ul>
               <li style="opacity: 0.5"><ion-icon name="alert-outline"></ion-icon>&nbsp;&nbsp;&nbsp;MHS Notices</li>
               <li><span><ion-icon name="fast-food-outline"></ion-icon></span>&nbsp;&nbsp;&nbsp;lunch</li>
               <li style="opacity: 0.5"><ion-icon name="car-outline"></ion-icon>&nbsp;&nbsp;&nbsp;Bus</li>
               <li style="opacity: 0.5"><ion-icon name="videocam-outline"></ion-icon>&nbsp;&nbsp;&nbsp;School Video</li>
             </ul>
      </div>


    </div>
  </div>
  
</template>

<script>
// import quote from "@/components/Quote";

// import axios from "axios";
import dayjs from "dayjs";

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
      },
      periodInfo: {period: '1', lower: '09:00', upper: '09:40', block:1}

    }
  },
  methods:
      {
        findPeriod(time) {
          if (time >= "0900" && time < "0940") {
            return {period: '1', lower: '09:00', upper: '09:40', block: 1}
          } else if (time >= "0940" && time < "1020") {
            return {period: '2', lower: '09:40', upper: '10:20', block: 2}
          } else if (time >= "1020" && time < "1050") {
            return {period: 'Break', lower: '10:20', upper: '10:50', block: 0}
          } else if (time >= "1050" && time < "1130") {
            return {period: '3', lower: '10:50', upper: '11:30', block: 3}
          } else if (time >= "1130" && time < "1210") {
            return {period: '4', lower: '11:30', upper: '12:10', block: 4}
          } else if (time >= "1210" && time < "1250") {
            return {period: '5', lower: '12:10', upper: '12:50', block: 5}
          } else if (time >= "1250" && time < "1340") {
            return {period: 'Lunch', lower: '12:50', upper: '13:40', block: 0}
          }else if (time >= "1340" && time < "1420") {
            return {period: '6', lower: '13:40', upper: '14:20', block: 6}
          }else if (time >= "1420" && time < "1500") {
            return {period: '7', lower: '14:20', upper: '15:00', block: 7}
          }else if (time >= "1500" && time < "1505") {
            return {period: 'Gap', lower: '15:00', upper: '15:05', block: 0}
          }else if (time >= "1505" && time < "1545") {
            return {period: '8', lower: '15:05', upper: '15:45', block: 8}
          }else if (time >= "1545" && time < "1550") {
            return {period: 'Gap', lower: '15:45', upper: '15:50', block: 0}
          }else if (time >= "1550" && time < "1630") {
            return {period: '9', lower: '15:50', upper: '16:30', block: 9}
          } else {
            return {period: 'N/a', lower: '16:30', upper: '09:00', block: 0}
          }
        },
        pollData() {
          this.polling = setInterval(() => {
            this.periodInfo = this.findPeriod(dayjs().format('HHmm'))
          }, 1000)
        },
        pullData() {
          this.periodInfo = this.findPeriod(dayjs().format('HHmm'))
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

.active-period {
  background-color: #F87474;
}

.inactive-period{
  background-color: #F9F2ED;
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
  background-color: #fbf8f5;
  border: 4px solid #e0d8d8;
  box-shadow: 0.1vh 0.1vh 1vh 1vh #fbf8f5;
}

.widget-rotation ul li span{
  padding-top: 0.5vh;
  color: #F87474;
}









</style>