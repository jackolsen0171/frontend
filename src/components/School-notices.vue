<template>
  <div class="school-notices">
<!--    <div class="school-overlay1 border-blue-shadow">-->
<!--      <div>🏫 School Notices</div>-->
<!--    </div>-->
<!--    <div class="school-overlay2 border-blue-shadow">-->
<!--      <ul>-->
<!--        <li>Nothing to see here!</li>-->
<!--      </ul>-->
<!--      <div class="school-ellipse1"></div>-->
<!--    </div>-->
<!--    <div class="school-overlay3 border-blue">-->
<!--      <ul>-->
<!--        <li>Nothing to see here!</li>-->
<!--      </ul>-->
<!--    </div>-->
<!--    <div class="school-overlay4 border-blue">-->
<!--      <ul>-->
<!--        <li>Nothing to see here!</li>-->
<!--      </ul>-->
<!--      <div class="school-ellipse2"></div>-->
<!--    </div>-->
<!--    <div class='school-notices-grid'>-->
<!--      <div class='school-notices-title'>School Notices</div>-->
<!--      <div class='school-notices-data'>-->
<!--        <div class=notice1>-->
<!--          <ul>-->
<!--            <li>2nd XI football team enjoy another big win and continue their unbeaten streak!</li>-->
<!--          </ul>-->
<!--        </div>-->
<!--        <div class=notice2>-->
<!--          <ul>-->
<!--            <li>Chicken Katsu Curry: Contender for Meal of the Year?</li>-->
<!--          </ul>-->
<!--        </div>-->
<!--        <div class=notice3>-->
<!--          <ul>-->
<!--            <li>New groundbreaking dashboard system being trialled in the CS department - Dubbed as a 'work of art'</li>-->
<!--          </ul>-->
<!--        </div>-->

<!--      </div>-->
<!--      <div class=school-notices-underline></div>-->
<!--    </div>-->
  </div>
</template>

<script>
export default {
  name: "School-notices"
}
</script>

<style scoped>
.border-blue{
  /*box-shadow: 0.2vh 0.2vh 2.5vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  box-shadow: 0 0 0.1vh 0.5vh #1d94d9, 0 0 0.1vh 0.9vh #4c2bed;
}

.border-blue-shadow{
  box-shadow: 0.2vh 0.2vh 0.1vh 0.2vh #1d94d9, 0.5vh 0.3vh 0.1vh 0.4vh #4c2bed, 0vh 0vh 3vh 2vh #1e1d1d;

}

.school-notices {
  overflow: hidden;
  grid-column: 20/31;
  grid-row: 1/11;
  display:grid;
  grid-template-rows:repeat(10, 1fr);
  grid-template-columns:repeat(10, 1fr);
  color: white;
  font-family: "Poppins", sans-serif;
  /*background-color: #3AB0FF;*/
  background-color: #F9F2ED;
  border: 2px solid #e0d8d8;
  box-shadow:0.4vh 0.4vh 0.1vh #3AB0FF;

}

.school-notices li {
  font-size: 1.2vh;
}

.school-overlay1{
  grid-row: 1/4;
  grid-column:1/5;
  background: #2a2828;
  border-bottom-right-radius: 2vh;

}

.school-ellipse1{
  background: linear-gradient(#1ccece, #2072d0);
  border-radius: 50%;
  width: 3vw;
  height: 5vh;
  position: relative;
  left: 13.5vw;
  top: 12.5vh;
  filter: blur(0.3vh);
  opacity: 0.5;


}

.school-ellipse2{
  background: linear-gradient(#1ccece, #2072d0);
  border-radius: 50%;
  width: 3vw;
  height: 5vh;
  left: 22vw;
  top: 4.5vh;
  position: relative;
  filter: blur(0.3vh);
  opacity: 0.5;



}

.school-overlay1 div{
  padding-top: 1vh;
  font-weight: bold;
  font-size: 2.3vh;

}


.school-overlay2{
  background: #2a2828;
  border-bottom-right-radius: 2vh;
  grid-row: 1/9;
  z-index:-1;
  position: relative;
  bottom: 0.5vh;
  grid-column: 1/6;
  overflow: hidden;
}

.school-overlay2 ul{
  position: relative;
  top: 10vh;
  font-weight: 500;
  line-height: 2.5vh;
  left: 1vw;
  font-size: 1.3vh;
  max-width: 14vw;
}

.school-overlay3{
  background: #2a2828;
  grid-row: 6/11;
  grid-column: 1/11;
  z-index:-2;
  border-top-right-radius: 2vh;

}

.school-overlay3 ul{
  position: relative;
  left: 17.5vw;
  top: 1vh;
  max-width:13vw;
  max-height:10vh;
  line-height: 2.5vh;
}

.school-overlay4{
  background: #2a2828;

  grid-row: 1/7;
  position: relative;

  left: 1vw;
  z-index: -3;
  border-top-left-radius: 2vh;
  grid-column: 3/11;
  border-top-right-radius: 2vh;
  overflow: hidden;

}

.school-overlay4 ul{
  position: relative;
  left: 10.5vw;
  top: 1vh;
  font-size: 1.3vh;
  max-width:12vw;
  font-weight: 500;
  line-height: 2.5vh;

}














.school-notices-grid {
  width: 100%;
  display: grid;
  grid-auto-columns: repeat(13, 1fr);
  grid-template-rows: repeat(10, 1fr);
}

.school-notices-title {
  grid-row: 1/4;
  grid-column: 1/14;
  padding-left: 1vw;
  font-family: "kanit", sans-serif;
  text-decoration: underline;
  font-size: 3vh;
}

.school-notices-data {
  grid-row: 3/8;
  grid-column: 1/14;
  display: flex;
  flex-direction: column;
  align-items: left;
  padding-left: 3vw;
  margin-top: 2vh;
  font-family: "kanit", sans-serif;
}

.notice1,
.notice2,
.notice3 {
  font-size: 1.5vh;
}

</style>