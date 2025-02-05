<template>
    <div class="homePage">

<div class="homeSection d-flex flex-row justify-space-between">

  <div class="one" style="margin-left: 30vh; gap: 3.6vh;">
    <strong style="color: aliceblue;font-size: 35px;">Hello I'm</strong>
    <h2>Omar Hasan</h2>
    <h3>Front end Web Developer</h3>
    <p class="par">
      Main area of my expertise is front-end development and everything related with this
      side of web. HTML CSS JS, Now, I am currently learning one of the front-end frameworks,
      Vue.js
    </p>
    
    <div class="d-flex align-center">
      <button class="downloadButton">DOWNLOAD CV 
      </button>
      <a style="display: none;" id="downloadLink"></a>
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
    .myImg{
      width: 30vh;
    }
.homePage {
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
    scroll-behavior: smooth;
    overflow: hidden;
  }

  .homeSection{
    margin-bottom: 5vh;
  }

  .one {
    display: flex;
    flex-direction: column;
  }
  .one h2{
    color: rgb(113, 230, 244);
    font-size: 40px;
  }
  .one h3{
      background: linear-gradient(to right, #88e4f0 10%, #66ebce 50%, #57d7a2 60%);
      font-size: 30px;
      color: aqua;
      font-weight: 600;
      text-fill-color: transparent;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      display: inline-block;
  }
  .one .par {
    color: aliceblue;
    width: 48%;
    font-size: 18px;
    line-height: 28px;
  }

  .myLinks a{
    color: aliceblue;
    font-size: 24px;
    text-decoration: none;
    padding-left: 15px;
  }
  .myLinks{
    margin-left: 185px;
    margin-top: -30px;
    transition: 0.3s ease;
  }
  .myLinks a:hover{
    color:aqua
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
    margin-top: 0.5vh;
  }

  .downloadButton:hover {
    background-color: aqua;
    color: black;
  }
</style>