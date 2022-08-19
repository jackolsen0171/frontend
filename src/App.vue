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

/*1 is background
2 is widget colour
3 is extra colour
4 is white
5 is border colour*/




:root{
  --color1: #1b1c1f;
  --color2: #272930;
  --color3: #2666CF;
  --color4: #F5F2E7;
  --color5: #F5F2E7;
  --borderWidth: 0.2vh;
}







* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}



.bg-main{
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: var(--color2);
  width: 100vw;
  height: 100vh;
}




.side-bar{
  height: 95vh;
  width: 25vw;
  position: relative;
  left: 0.75vw;
  border-radius: 2vh;
  z-index:1;
  border: var(--borderWidth) solid #333b40;


}



.grid-container {
  border: var(--borderWidth) solid #333b40;
  width: 70vw;
  height: 95vh;
  display: grid;
  grid-template-columns: repeat(30, 1fr);
  grid-template-rows: repeat(30, 1fr);
  gap: 3vh;
  padding: 3vh;
  border-radius: 2vh;
  background: var(--color1);
  overflow: hidden;
  color: var(--color4);


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
  border: 0.2vh solid var(--color4);
  width: 4.5vw;
  height: 1.5vh;
  border-radius: 50%;
  border-bottom: transparent;
  /*opacity: 0.7;*/
  /*filter: blur(0.1vh);*/


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
  border: 0.2vh solid var(--color3);
  width: 0.5vw;
  height: 1vh;
  border-radius: 50%;
  /*opacity: 0.7;*/
  /*filter: blur(0.1vh);*/


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
  border: 0.2vh solid var(--color3);
  width: 0.5vw;
  height: 1vh;
  border-radius: 50%;
  /*opacity: 0.7;*/
  /*filter: blur(0.1vh);*/
}




</style>
