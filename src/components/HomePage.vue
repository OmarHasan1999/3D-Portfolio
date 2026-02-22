<template>
    <div class="homePage">

<div class="homeSection d-flex flex-row justify-space-between">

  <div class="one">
    <strong class="strong" style="color: aliceblue;font-size: 35px;">Hello I'm</strong>
    <h2 class="name">Omar Hasan</h2>
    <h3>Front end Web Developer</h3>
    <p class="par">
      Front-end focused (HTML, CSS, JS) and currently exploring Vue.js
    </p>
    
    <div class="d-flex align-center allLinks">
      <button class="downloadButton">DOWNLOAD CV 
      </button>
      <a style="display: none;" id="downloadLink"></a>

      <div class="myLinks d-flex">
                <a href="https://github.com/OmarHasan1999" target="blank"><v-icon>mdi-github</v-icon></a>
                <a href="https://www.linkedin.com/in/omar-hasan-a633aa252/" target="blank"><v-icon>mdi-linkedin</v-icon></a>
                <a href="https://www.facebook.com/omar.hamad.18294" target="blank"><v-icon>mdi-facebook</v-icon></a>
                <a href="https://www.instagram.com/omar._.hasan/" target="blank"><v-icon>mdi-instagram</v-icon></a>
      </div>

    </div>
  </div>

</div>



</div>


</template>


<script>
export default {
    
}
</script>
<style lang="css">
.homePage {
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
    scroll-behavior: smooth;
    overflow: hidden;
  }

  .one {
    display: flex;
    flex-direction: column;
    gap: 1vh;
    padding-left: 250px;
    padding-top: 20px;
  }
  .one h2{
    color: rgb(113, 230, 244);
    font-size: 40px;
  }
  .one h3{
      background: linear-gradient(to right, #88e4f0 10%, #66ebce 50%, #57d7a2 60%);
      font-size: 30px;
      color: aqua;
      font-weight: 900;
      text-fill-color: transparent;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      display: inline-block;
  }
  .one .par {
    color: aliceblue;
    width: 85%;
    font-size: 18px;
    line-height: 28px;
    padding-bottom: 12px;
  }

  .myLinks a{
    color: aliceblue;
    font-size: 20px;
    text-decoration: none;
    padding-left: 15px;
    pointer-events: auto;
  }
  .myLinks{
    margin-left: 32px;
    transition: 0.3s ease;
  }
  .myLinks a:hover{
    color:aqua;
  }

  .downloadButton {
    background-color: transparent;
    border: 1px solid aqua;
    border-radius: 20px;
    color: aqua;
    padding: 9px 30px;
    font-weight: 700;
    text-align: center;
    border-left-width: 2px;
    border-right-width: 2px;
    cursor: pointer;
    pointer-events: auto;
  }

  .downloadButton:hover {
    background-color: aqua;
    color: black;
  }

  /* Responsive section */

  @media (max-width:1200px){
    .one {
    gap: 2vh;
    padding-left: 200px;
    padding-top: 20px;
  }
    .one .par {
    padding-bottom: 25px;
  }
  }

  @media (max-width:1024px){
    .one {
    gap: 2vh;
    padding-top: 50px;
    padding-right: 100px;
  }
    .one .par {
    padding-bottom: 25px;
  }
  }

  @media (max-width:991px){
    .one{
        gap: 2vh;
        padding-bottom: 120px;
        padding-right: 100px;
    }
  }

  @media (max-width:900px){
        .one .par{
      width: 60%;
    }
    .one{
        gap: 2vh;
        padding-right: 150px;
    }
  }

  @media (max-width:768px){
   .one{
    align-items: center;
    justify-content: center;
    gap: 2vh;
    padding-top: 130px;
    padding-left: 0;
    padding-right: 0;
    text-align: center;
    width: 100%;
   }
   
   .one h2,
   .one h3,
   .one .strong,
   .one .par {
    margin: 0;
    padding: 0 20px;
   }
   
   .one .par {
    width: 100%;
    padding: 0 20px;
    box-sizing: border-box;
   }
   
   /* .allLinks {
    justify-content: center;
    flex-direction: column;
    align-items: center;
    gap: 1.5vh;
   } */
   
   .myLinks {
    margin-left: 0;
    justify-content: center;
   }
  }
/*
  @media (max-width:617px){
    .one .strong{
      font-size: 30px !important;
      margin-left: -11vh !important;
      font-weight: 700;
    }
    .one h2{
      margin-left: -11vh !important;
      margin-top: 1.7vh !important;
    }
    .one h3{
      font-weight: 900 !important;
      font-size: 18px !important;
      margin-left: -11vh !important;
  }
  .one .par{
      text-align: left !important;
      font-size: 16px !important;
      line-height: 25px !important;
      margin-left: -11vh !important;
      width: 55%

    }
    .downloadButton{
      margin-left: -11vh !important; 
  }
  }

  @media (max-width:450px){
    .one h2{
      margin-left: 0vh !important;
      margin-top: -6vh !important;
      font-weight: 700 !important
    }
    .one h3{
      font-weight: 700 !important;
      font-size: 14px !important;
  }
    .one .par{
      font-size: 16px !important;
      line-height: 25px !important;
      width: 70%;

    }
  }

  @media (max-width:375px){
    
    
    .one {
    gap: 1vh !important;
    margin-top: -4.4vh !important;
  }
    .one .strong{
      font-size: 25px !important;
      margin-top: -17vh !important;
      margin-left: 2vh !important;
      font-weight: 700;
    }
    .one h2{
      margin-top: -12.8vh !important;
      margin-left: 12.5vh !important;
    }
    
    .one h3{
      margin-left: -12.8vh !important;
      margin-bottom: 5vh !important;
  }
  .one .par{
      width: 100%;
      font-size: 15px !important;
      text-align: center !important;
      margin-top: -4.8vh;
      margin-left: -10vh !important;
      font-weight: 600;
      color: rgb(228, 248, 247);
    }
     .downloadButton{
      padding: 5px 14px !important ;
      font-size: 12px !important;
      font-weight: 700 !important;
      margin-bottom: -15vh !important;
      margin-top: -20vh !important;
      margin-left: -28vh !important; 
      margin-right: 44vh !important; 
  }
  .myLinks{
      margin-top: -5vh !important;
      margin-left: -45vh !important;
  }
  .myLinks a{
      font-size: 16px !important; 
      margin-right: -1vh;
  } 
  .allLinks{
    margin-top: 7vh;
    margin-left: 16vh;
  }
  }

  
  @media (max-width:320px){
    .one .strong{
      margin-top: -15vh !important;
      margin-left: -3vh !important;
      font-weight: 700;
    }
    .one h2{
      margin-top: -12.3vh !important;
      margin-left: 16vh !important;
      font-weight: 600 !important;
    }
    .one h3{
      margin-left: -13.6vh !important;
      font-weight: 300 !important;
  }
  .one .par{
      width: 130%;
      margin-left: -13.5vh !important;
    }
    .downloadButton{
      padding: 5px 10px !important ;
      font-size: 10px !important;
      font-weight: 900 !important;
      margin-left: -32vh !important; 
      margin-right: 44vh !important; 
  }
  .myLinks a{
      font-size: 14px !important; 
      margin-right: -1vh;
  }
    
/*     
    .one {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8vh !important;
  }
    .one .strong{
      font-size: 25px !important;
      margin-top: -8.5vh;
      margin-bottom: -5vh;
      margin-left: -23vh;
      font-weight: 700;
    }
    .one h2{
      margin-top: -5vh !important;
      margin-bottom: -5vh !important;
    }
    
    .one h3{
      font-weight: 600;
      font-size: 18px;
      margin-left: -2vh !important;
      margin-bottom: -2vh !important;
  }
  .one .par{
      width: 150%;
      font-size: 15px;
      text-align: center;
      margin-top: -4vh;
      font-weight: 700;
      color: rgb(228, 248, 247);
    }
     .downloadButton{
      padding: 5px 14px !important ;
      font-size: 12px !important;
      font-weight: 700 !important;
      margin-bottom: -15vh !important;
      margin-top: -20vh !important;
      margin-left: -28vh !important; 
      margin-right: 44vh !important; 
  }
  .myLinks{
      margin-top: -5vh !important;
      margin-left: -45vh !important;
  }
  .myLinks a{
      font-size: 16px !important; 
      margin-right: -1vh;
  }
*/
/* } */

 
</style>