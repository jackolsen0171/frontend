<template>
  <div class="fixtures">
    <div class="fixtures-overlay1 border-blue">
      <div class="fixture-container">
        <div class="ellipse1"></div>
        <div>Sport Fixtures 🏅</div>
        <div class="sport"><span
            style="position:relative;top: 5vh;overflow: hidden;right:0vw ">{{ fixtures[fixturePos].emoji || ''}}</span>️
        </div>
        <div class="team"><span style="opacity: 0.5;font-weight: 200">Team: </span><span
            style="display: block; font-size: 2.3vh">{{ fixtures[fixturePos].team || 'No Current Upcoming Fixtures'}}</span></div>
        <div class="line"></div>
        <div class="date">{{ fixtures[fixturePos].dateFormat || ''}}<span style="position: relative;left: 3vw">{{ fixtures[fixturePos].sport || ''}}<span
            style="font-size:2vh;font-weight: 800; ">:</span></span></div>
        <div class="opposition"><span style="opacity: 0.5;font-weight: 200">Opposition: </span><span
            style="display: block;width: 21vw;" :class="fixtures[fixturePos].opponent.length > 25 ? 'small-team' : 'reg-team'">{{ fixtures[fixturePos].opponent|| '' }}</span></div>
      </div>
    </div>
    <div class="fixtures-overlay2 border-blue">
      <div class="key-dates-container">
        <div class="ellipse2"></div>
        <div>Key Dates 🗓</div>
        <div class="key-dates-date">{{ dates[datesPos].dateArr[0] }} {{ dates[datesPos].dateArr[2] }} {{ dates[datesPos].dateArr[1] }}</div>
        <div class="key-date-info">
          {{ dates[datesPos].title }}
        </div>
      </div>

    </div>

  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Fixtures",
  data() {
    return {
      polling: null,
      fixturePos: 0,
      fixtures: [{
        emoji: '',
        team: 'No Current Upcoming Fixtures',
        dateFormat: '',
        sport:'',
        opponent:''

      }],
      datesPos:0,
      dates: []
    }
  },
  methods: {
    pullData() {
      axios.get('https://fathomless-crag-41517.herokuapp.com/fixtures').then(response => (this.fixtures = response.data))
      axios.get('https://fathomless-crag-41517.herokuapp.com/dates').then(response => (this.dates = response.data))
    },
    getPos() {
      this.polling = setInterval(() => {
        this.fixturePos >= this.fixtures.length ? this.fixturePos = 0 : this.fixturePos += 1
        this.datesPos >= this.fixtures.length ? this.datesPos = 0 : this.datesPos += 1
      }, 4000)
    }
  },
  mounted() {
    this.pullData()
  },
  beforeDestroy() {
    clearInterval(this.polling)
  },
  created() {
    this.getPos()
  }
}
</script>

<style scoped>

.small-team{
  font-size: 1.7vh;
}

.reg-team{
  font-size: 2.3vh;
}

.border-blue {
  /*box-shadow: 0.2vh 0.2vh 2.5vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  box-shadow: 0 0 0.1vh 0.4vh #1d94d9, 0 0 0.1vh 0.7vh #4c2bed;
  /*box-shadow: 0.2vh 0.2vh 0.3vh 0.6vh #7dc5ef,  0.2vh 0.2vh 0.7vh 0.6vh #4587e4,  0.2vh 0.2vh 1vh 0.6vh #0861ef*/

}

/*.ellipse1{*/
/*  !*background: linear-gradient(#1ccece, #2072d0);*!*/
/*  border-radius: 50%;*/
/*  border-left: 0.6vh solid #2196f3;*/
/*  width: 5vw;*/
/*  height: 10vh;*/
/*  position: absolute;*/
/*  left: 13vw;*/
/*  top: 5vh;*/

/*}*/
/*.ellipse2{*/
/*  !*background: linear-gradient(#1ccece, #2072d0);*!*/
/*  border-radius: 50%;*/
/*  border: 0.2vh solid white;*/
/*  width: 3vw;*/
/*  height: 5vh;*/
/*  position: absolute;*/
/*  left: 9.5vw;*/
/*  top: 17vh;*/
/*}*/

.fixtures {
  grid-row: 22/31;
  grid-column: 12/24;
  background-color: #2a2828;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: repeat(12, 1fr);
  overflow: hidden;
  color: white;
  font-family: "Poppins", sans-serif;
}

/*which sport,  date, team, opponent*/
.fixtures-overlay1 {
  grid-row: 1/13;
  grid-column: 1/8;
  border-radius: 2vh;
  position: relative;
  left: -0.2vw;
  overflow: hidden;
  width: 24vw;

}

.fixtures-overlay2 {
  grid-row: 1/13;
  grid-column: 9/13;
  border-bottom-left-radius: 2vh;
  border-top-left-radius: 2vh;
}

.fixture-container {
  position: relative;
  left: 1.3vw;
  top: 1vh;
  font-size: 3vh;
  width: 14.5vw;
  height: 18vh;

}


.date {
  font-size: 2vh;
  position: relative;
  left: 0vw;
  bottom: 5.5vh;
  font-weight: 300;
}


.line {
  height: 0.1vh;
  width: 12vw;
  background: white;
  position: relative;
  top: 6.5vh;
}

.sport {
  position: absolute;
  left: 14vw;
  bottom: 3vh;
  font-size: 10vh;
}

.team {
  font-size: 1.5vh;
  position: relative;
  top: 6vh;

}

.opposition {
  font-size: 2vh;
  position: relative;
  top: 4vh;
}


.key-dates-container {
  position: relative;
  left: 0.75vw;
  top: 1vh;
  font-size: 2.7vh;
  width: 12vw;
  height: 18vh;
}

.key-dates-date {

  font-size: 2vh;
  font-weight: 200;
}

.key-date-info {
  font-size: 1.5vh;
  padding-top: 1.5vh;
  max-width: 10vw;


}


</style>