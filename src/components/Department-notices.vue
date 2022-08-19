<template>
  <div class='department-notices'>
    <div class="title">Department Notices <ion-icon style="position: relative;top: 0.6vh" name="alert-outline"></ion-icon></div>
    <div class="teacher-rotation">
      <p style="opacity: 0.5" >Mr Olsen</p>
      <p style="opacity: 0.5">Mr Gal</p>
      <p>Dr Mookle</p>
    </div>
    <div class="notices">
      <li class="notice1">Hi Students. Myself, Mookle 420 won't be able to attend todays lesson. You will have Mr Raj as a cover.</li>
      <li class="notice2">Nothing to see here!</li>
<!--          <img class='notice1' src="@/assets/sticky-note.png" alt="loading....">-->
<!--          <img class='notice2' src="@/assets/sticky-note.png" alt="loading....">-->
    </div>
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
  /*border: var(--borderWidth) solid var(--color5);*/
  /*background: var(--color2);*/
  border-radius: 2vh;
  grid-column: 17/31;
  grid-row: 15/31;
  font-family: "Poppins", sans-serif;
  display: grid;
  grid-template-columns: repeat(15, 1fr);
  grid-template-rows: repeat(15, 1fr);
  border-left: var(--borderWidth) solid var(--color5);
  border-right: var(--borderWidth) solid var(--color5);


}

.title{
  font-size: 4.4vh;
  grid-row: 1/3;
  grid-column: 1/17;
  font-weight: 200;
  position: relative;
  left: 1vw;
  top: 2vh;
}

.teacher-rotation{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  grid-row: 5/7;
  grid-column: 1/15;
  position: relative;
  left: 1vw;
  font-size: 2.5vh;
  font-weight: 200;
}


.teacher-rotation p:nth-child(3){
  height: 4vh;
  width: 8vw;
  text-align: center;
  border-radius: 10vh;
  background-color: #F9F2ED;
  color: var(--color1);
}

.notices{
  grid-column: 1/16;
  grid-row: 7/16;
  display: flex;
  flex-direction: row;
  justify-content: space-around;



}

.notices > li{
  width: 17vw;
  height:90%;
  border-radius: 0.5vh;
  padding: 1vh;
  font-size: 2vh;
  list-style: none;
  position: relative;
  left: 0.5vw;
  font-weight: 100;
}

.notices > li::before{
  content: "\2022";
  color: var(--color3);
  font-weight: bold;
  display: inline-block;
  width: 1em;
}

/*.notice1{*/
/*  !*border-left: 2px solid rgba(255, 181, 98,0.7);*!*/
/*  border-right: 2px solid var(--color3);*/
/*}*/

/*.notice2{*/
/*  border-left: 2px solid var(--color3);*/
/*  !*border-right: 2px solid rgba(248, 116, 116,0.7);*!*/
/*}*/

</style>