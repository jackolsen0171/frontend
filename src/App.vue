<template>
  <div id="app">
    <div class="bg-main">
      <div class="ring-binders">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>

      </div>
      <div class="ring-binders2">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>

      </div>
      <div class="ring-binders3">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
      </div>
      <side-bar class="side-bar"></side-bar>
      <div class="grid-container">
        <dateTime></dateTime>
  

<!--        <div class="img-container"><img src="@/assets/Mill_Hill_School_Coat_of_Arms_(2017).png"></div>-->
        <department-notices></department-notices>
        <weather></weather>
        <news></news>
<!--        <school-notices class="color-widget"></school-notices>-->
        <!--      <p>&copy; J.Olsen & Y.Gal 2021-Present</p>-->
      </div>
    </div>
  </div>
</template>
<script>
// import Bus from './components/Bus.vue'
import news from "@/components/News";
import departmentNotices from "@/components/Department-notices";
import weather from "@/components/Weather";
import sideBar from "@/components/sideBar";
import dateTime from "@/components/Date,time,quote"
// import schoolNotices from "@/components/School-notices"


export default {
  name: 'App',
  components: {
    sideBar,
    // Bus,
    news,
    departmentNotices,
    weather,
    dateTime,
    // schoolNotices,


  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Oswald');
@import url("https://fonts.googleapis.com/css2?family=Dongle:wght@300&family=Kanit:wght@300&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Dongle:wght@300&family=Kanit:wght@300&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
@import url('https://fonts.googleapis.com/css2?family=Rowdies&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;






}

#app {
  /*
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  */
}

.bg-main{
  display: flex;
  justify-content: space-around;
  align-items: center;
  /*background-color: #272748;*/
  background-color: #F9F2ED;
  width: 100vw;
  height: 100vh;
}

.bg-main::before{
  /*content: '';*/
  /*position: absolute;*/
  /*top: 0;*/
  /*left: 0;*/
  /*right: 0;*/
  /*bottom: 0;*/
  /*box-shadow: inset 0 0 4vh rgba(255, 255, 255, 0.5);*/
  /*filter: blur(3vh);*/
  /*background: linear-gradient( to bottom,#af0808, #9a609a);*/
  /*opacity: 0.5;*/
  /*clip-path: circle(30% at right 70%);*/
}



.side-bar{
  height: 95vh;
  width: 25vw;
  position: relative;
  left: 0.75vw;
  border-radius: 2vh;
  z-index:1;
}



.grid-container {
  width: 70vw;
  height: 95vh;
  display: grid;
  grid-template-columns: repeat(30, 1fr);
  grid-template-rows: repeat(30, 1fr);
  gap: 2.5vh;
  padding: 3vh;
  border-radius: 2vh;
  background: white;
  border: 2px solid #e0d8d8;
  overflow: hidden;

}




.widget {
  z-index: 1;
  border-radius: 2vh;
  backdrop-filter: blur(0.5vh);
  border: 2px solid #e0d8d8;
  background-color: #F9F2ED;


}

.ring-binders{
  width: 5vw;
  height: 89vh;
  position: absolute;
  top: 6vh;
  left: 26vw;
  z-index: 2;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.ring-binders > div{
  border: 0.2vh solid black;
  width: 4.5vw;
  height: 1.5vh;
  border-radius: 50%;
  border-bottom: transparent;
  opacity: 0.7;
  filter: blur(0.1vh);


}

.ring-binders2{
  width: 5vw;
  height: 89vh;
  position: absolute;
  top: 6.5vh;
  left: 26vw;
  z-index: 2;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.ring-binders2 > div{
  border: 0.2vh solid grey;
  width: 0.5vw;
  height: 1vh;
  border-radius: 50%;
  opacity: 0.7;
  filter: blur(0.1vh);


}

.ring-binders3{
  width: 5vw;
  height: 89vh;
  position: absolute;
  top: 6.5vh;
  left: 30vw;
  z-index: 2;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.ring-binders3 > div{
  border: 0.2vh solid grey;
  width: 0.5vw;
  height: 1vh;
  border-radius: 50%;
  opacity: 0.7;
  filter: blur(0.1vh);
}

.page-divider{
  /*width: 3vw;*/
  /*height: 5vh;*/
  width: 70vw;
  height: 100vh;
  grid-row: 17/31;
  grid-column: 1/31;
  position: relative;
  top: 1.65vh;
  right: 1.75vw;
  border-radius:7vh;
  /*box-shadow: 0 0 0.1vh 0.6vh #FFB562, 0 0 0.1vh 1.2vh #3AB0FF;*/
}


</style>
