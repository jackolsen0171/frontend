<template>
  <div class='department-notices'>
<!--    <img class='notice1' src="@/assets/sticky-note.png" alt="loading....">-->
<!--    <img class='notice2' src="@/assets/sticky-note.png" alt="loading....">-->
    <!--    <img src="@/assets/Mill_Hill_School_Coat_of_Arms_(2017).png">-->



<!--    <div class="triangles">-->
<!--      <div class="triangle1"></div>-->
<!--      <div class="triangle2"></div>-->
<!--      <div class="triangle3"></div>-->
<!--    </div>-->
<!--    <div class="teacher-rotation">-->
<!--      <div class="title">Department Notices</div>-->
<!--      <div class="teachers">-->
<!--        <div>Mr Olsen</div>-->
<!--        <div>Mr Gal</div>-->
<!--        <p>Dr Mookle</p>-->
<!--      </div>-->
<!--    </div>-->
<!--    <div class="notices-container">-->
<!--      <div class="department-notice1">-->
<!--        <ion-icon name="alert-circle-outline"></ion-icon>️&nbsp;Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris pharetra ligula sit amet enim aliquam feugiat. Integer pulvinar ipsum eu.-->
<!--      </div>-->
<!--      <div class="department-notice2">-->
<!--        <ion-icon name="alert-circle-outline"></ion-icon>️&nbsp;Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris pharetra ligula sit amet enim aliquam feugiat. Integer pulvinar ipsum eu.-->
<!--      </div>-->
<!--    </div>-->
<!--    <div class="main-notice-container">-->
<!--      <div class="main-notice-title"><ion-icon name="alert-outline"></ion-icon>&nbsp;Room Change</div>-->
<!--      <ul class="main-notice">-->
<!--        <li>bla bla bla i cant think of any thing to say to act as filler text. lorem ipsum.</li>-->
<!--      </ul>-->

<!--    </div>-->
<!--    <img class="cork-board" src="@/assets/cork-board.jpeg">-->

  </div>

</template>

<script>
import dayjs from 'dayjs'

export default {
  name: "Period",
  data() {
    return {
      polling: null,
      polledData: {period: 'Period', range: 'loading...'}
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(() => {
        const now = new dayjs().format('HHmm')
        const day = new dayjs().day()
        this.polledData = this.findPeriod(now, day)
      }, 60000)
    },
    findPeriod(time, day) {
      if (day === 5 || day === 6) {
        return {period: 'N/a', range: 'Weekend'}
      } else if (time >= "0900" && time < "0940") {
        return {period: '1', range: '09:00 - 09:40'}
      } else if (time >= "0940" && time < "1020") {
        return {period: '2', range: '09:40 - 10:20'}
      } else if (time >= "1020" && time < "1050") {
        return {period: 'Break', range: '10:20 - 10:50'}
      } else if (time >= "1050" && time < "1130") {
        return {period: '3', range: '10:50 - 11:30'}
      } else if (time >= "1130" && time < "1210") {
        return {period: '4', range: '11:30 - 12:10'}
      } else if (time >= "1210" && time < "1250") {
        return {period: '5', range: '12:10 - 12:50'}
      } else if (time >= "1250" && time < "1340") {
        return {period: 'Lunch', range: '12:50 - 13:40'}
      } else if (time >= "1340" && time < "1420") {
        return {period: '6', range: '13:40 - 14:20'}
      } else if (time >= "1420" && time < "1500") {
        return {period: '7', range: '14:20 - 15:00'}
      } else if (time >= "1500" && time < "1505") {
        return {period: 'Gap', range: '15:00 - 15:05'}
      } else if (time >= "1505" && time < "1545") {
        return {period: '8', range: '15:05 - 15:45'}
      } else if (time >= "1545" && time < "1550") {
        return {period: 'Gap', range: '15:45 - 15:50'}
      } else if (time >= "1550" && time < "1630") {
        return {period: '9', range: '15:50 - 16:30'}
      } else {
        return {period: 'N/a', range: '16:30 - 09:00'}
      }
    }
  },
  mounted() {
    const now = new dayjs().format('HHmm')
    const day = new dayjs().day()
    this.polledData = this.findPeriod(now, day)
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
.department-notices {
  grid-column: 2/31;
  grid-row: 15/23;
  background-color: #F9F2ED;
  border: 2px solid #e0d8d8;
}


.notices > div {
  width:25vw;
  height: 22vh;
  color: white;
  font-family: "Poppins", sans-serif;
  background-color: #F9F2ED;
  border: 2px solid #e0d8d8;
}

.notice1{
  transform: rotate(-5.75deg);
}

.notice2{
  position: relative;
  left: 17.5vw;
  bottom: 29vh;
  transform: rotate(-5.75deg);
}


/*.teacher-rotation{*/
/*  !*border: 2px solid #e0d8d8;*!*/
/*  width: 25vw;*/
/*  height: 20vh;*/
/*  !*background-color: #F9F2ED;*!*/
/*  !*background-color: white;*!*/
/*  !*z-index: 1;*!*/
/*  border-radius: 2vh;*/
/*  position: relative;*/
/*  display: grid;*/
/*  grid-template-columns: repeat(10,1fr);*/
/*  grid-template-rows: repeat(10,1fr);*/
/*  !*left: -1vw;*!*/
/*}*/
/*.title{*/
/*  font-family: "Poppins", sans-serif;*/
/*  font-size: 4.5vh;*/
/*  font-weight: 600;*/
/*  grid-column: 1/11;*/
/*  grid-row: 1/2;*/


/*}*/

/*.teachers{*/
/*  display: flex;*/
/*  flex-direction: row;*/
/*  justify-content: space-between;*/
/*  font-family: "Poppins", sans-serif;*/
/*  font-size: 2.3vh;*/
/*  grid-column: 1/11;*/
/*  grid-row: 3/4;*/
/*  font-weight: 600;*/
/*}*/



/*.teachers p::after{*/
/*  content: '';*/
/*  position: absolute;*/
/*  top: 11.5vh;*/
/*  left: 19vw;*/
/*  width: 4vw;*/
/*  height: 0.25vh;*/
/*  background: #3AB0FF;*/
/*}*/

/*.teachers div{*/
/*  opacity: 0.5;*/
/*}*/


/*.main-notice-title ion-icon{*/
/*  color: red;*/
/*  font-size: 5vh;*/
/*  position: absolute;*/
/*  top: 1.5vh;*/
/*  left: 0.5vw;*/

/*}*/

/*.notices-container{*/
/*  grid-row: 2/11;*/
/*  width: 33vw;*/
/*  font-family: "Poppins", sans-serif;*/
/*  position: relative;*/
/*  bottom: 6vh;*/
/*  display: flex;*/
/*  flex-direction: row;*/
/*  justify-content: space-between;*/
/*  font-size: 2vh;*/
/*  !*border: 2px solid red;*!*/
/*}*/


/*.notices-container div{*/
/*  width: 15vw;*/
/*}*/



/*!*.triangles{*!*/
/*!*  opacity: 0.7;*!*/
/*!*}*!*/

/*!*.triangle1 {*!*/
/*!*  width: 0;*!*/
/*!*  height: 0;*!*/
/*!*  border-left: 0.75vh solid transparent;*!*/
/*!*  border-right: 0.75vh solid transparent;*!*/
/*!*  border-bottom: 1.5vh solid #3AB0FF;*!*/
/*!*  position: absolute;*!*/
/*!*  left:33vw;*!*/
/*!*  top: 54vh;*!*/
/*!*  transform: rotate(-45deg);*!*/
/*!*}*!*/

/*!*.triangle2 {*!*/
/*!*  width: 0;*!*/
/*!*  height: 0;*!*/
/*!*  border-left: 0.75vh solid transparent;*!*/
/*!*  border-right: 0.75vh solid transparent;*!*/
/*!*  border-bottom: 1.5vh solid #FFB562;*!*/
/*!*  position: absolute;*!*/
/*!*  left:1vw;*!*/
/*!*  top: 54vh;*!*/
/*!*  transform: rotate(-346deg);*!*/
/*!*}*!*/


/*!*.triangle3 {*!*/
/*!*  width: 0;*!*/
/*!*  height: 0;*!*/
/*!*  border-left: 0.75vh solid transparent;*!*/
/*!*  border-right: 0.75vh solid transparent;*!*/
/*!*  border-bottom: 1.5vh solid #F87474;*!*/
/*!*  position: absolute;*!*/
/*!*  left:32vw;*!*/
/*!*  top: 4vh;*!*/
/*!*  transform: rotate(70deg);*!*/


/*!*}*!*/

/*.cork-board{*/
/*  width: 100%;*/
/*  height: 100%;*/
/*  position: absolute;*/
/*  border-radius: 2vh;*/
/*  opacity: 0.8;*/
/*  filter: blur(0.1vh);*/
/*}*/

/*.sticky-note{*/
/*  z-index: 1;*/
/*  position: absolute;*/
/*  top: 4vh;*/
/*  left: 0.5vw;*/
/*  transform: rotate(-5.9deg);*/
/*}*/

/*.sticky-note2{*/
/*  z-index: 1;*/
/*  position: absolute;*/
/*  top: 4vh;*/
/*  left: 17.5vw;*/
/*  transform: rotate(-5.9deg);*/
/*}*/


</style>