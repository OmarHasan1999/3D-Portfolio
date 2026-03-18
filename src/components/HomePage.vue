<template>
    <div class="homePage">

<div class="homeSection">

  <div class="one">
    <strong>Hello I'm</strong>
    <h2 class="name">Omar Hasan</h2>
    <h3>Front end Web Developer</h3>
    <p class="par">
      Front-end focused (HTML, CSS, JS) and currently exploring Vue.js
    </p>
    
    <div class="allLinks">
      <button class="downloadButton">DOWNLOAD CV</button>
      <a style="display: none;" id="downloadLink"></a>

      <div class="myLinks">
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
    height: 100vh;
    margin: 0;
    padding: 0;
  }

.homeSection {
    width: 100%;
    height: 100vh;          
    display: flex;
    flex-direction: row;
    align-items: center;       
    justify-content: space-between;
    padding: 0 5vw; 
}

  .one {
    display: flex;
    flex-direction: column;
    gap: 1vh;
    padding-left: 100px;
    padding-top: 10vw;
    max-width: 100%;
    z-index: 1;
  }
  .one strong {
    color: aliceblue;
    font-size: clamp(24px, 2.5vw, 35px);      
}
  .one h2{
    color: rgb(113, 230, 244);
    font-size: clamp(30px, 4vw, 42px);
    width:fit-content;
  }
  .one h3{
      background: linear-gradient(to right, #88e4f0 10%, #66ebce 50%, #57d7a2 60%);
      font-size: clamp(22px, 2.5vw, 32px);
      color: aqua;
      font-weight: 900;
      background-size: 200% auto;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      display: inline-block;
  }
  .one .par {
    color: aliceblue;
    width: 80%;
    font-size: clamp(20px, 1.5vw, 18px);
    line-height: 1.7;
    padding-bottom: 12px;
  }

  .allLinks {
    display: flex;
    align-items: center;
    gap: 12px;
}

    .myLinks{
    display: flex;
    margin-left: 20px;
    gap: 4px;
    transition: 0.3s ease;
  }

  .myLinks a{
    color: aliceblue;
    font-size: 22px;
    text-decoration: none;
    padding-left: 15px;
    pointer-events: auto;
    transition: color 0.2s ease;
  }

  .myLinks a:hover{
    color:aqua;
  }

  .downloadButton {
    background-color: transparent;
    border: 2px solid aqua;
    border-radius: 20px;
    color: aqua;
    padding: 9px 30px;
    font-size: 16px;
    font-weight: 700;
    cursor: pointer;
    pointer-events: auto;
    transition: background-color 0.2s ease, color 0.2s ease;
    white-space: nowrap;
  }

  .downloadButton:hover {
    background-color: aqua;
    color: black;
  }

  /* Responsive section */
  @media (max-width:1200px) {    
    .one {
      gap:3vh;
    }
    .allLinks {
      gap: 0px;
      padding-top: 15px;
    }
    .one strong {
      font-size: 28px;
    }
     .one h2 {
      font-size: 36px;
    }
     .one h3 {
      font-size: 24px;
    }
     .one .par {
      width: 75%;
      font-size: 18px;
    }
     .downloadButton{
      padding: 9px 20px;
      font-size: 16px !important;
      font-weight: 600 !important;
    }
  }
  @media (max-width:991px) {
    .one {
      gap: 2vh;
      padding-left: 6vw;
    }
    .allLinks {
      gap: 0px;
    }
    .downloadButton{
      padding: 9px 20px;
      font-size: 16px !important;
      font-weight: 600 !important;
    }
    .one .par {
      width: 75%;
    }
  }

  @media (max-width:768px){
    .homeSection {
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        padding: 0 24px;
        padding-bottom: 16vw;
    }

    .one {
        align-items: center;     
        padding: 0 0 0vw 0 !important;
        max-width: 520px;
        width: 100%;
        gap: 8px;
    }
    .one strong {
        font-size: 28px;
        display: block;
        text-align: center;
        width: 100%;
    }
    .one .par {
        width: 80%;
        text-align: center;
        font-size: 18px;
        padding: 0 0 10px 0;
    }

    .one h2 {
        font-size: 30px;
        width: 100%;
        text-align: center;
    }

    .one h3 {
        font-size: 24px;
        display: block;        
        width: 100%;
        text-align: center;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
    }

    .allLinks {
        flex-direction: row;
        justify-content: center;
        align-items: center;
        gap: 12px;
        padding:0;
        width: 100%;
    }

    .myLinks {
        margin-left: 0;
        gap: 1px;
        padding: 0;
        display: flex;
        justify-content: center;
    }

    .myLinks a {
        padding-left: 10px;
        font-size: 24px;          
    }
    .downloadButton {
        padding: 8px 30px;
        font-size: 14px;
    }
  }

  @media (max-width:600px){
    .one{
      gap:2px;
    }
    .allLinks{
      flex-direction: column;
      gap: 12px;
      padding: 0;
      margin-top: 1.5vw;
    }
    .downloadButton {
      padding: 6px 28px;
      font-size: 14px;
    }
    .one .par{
      width: 70%;
      padding: 0;
    }
  }
  @media (max-width:480px){
    .one h2{
      font-size: 26px;
    }
    .one h3{
      font-size: 21px;
    }
    .one .par{
      font-size: 16px;
    }
    .downloadButton {
      padding: 6px 22px;
      font-size: 10px;
    }
    .myLinks a {
      font-size: 20px;
      padding-left: 10px;
    }
  }

  @media (max-width:400px){
    .one h2{
      font-size: 24px;
    }
    .one h3{
      font-size: 18px;
    }
    .one .par{
      font-size: 16px;
      width: 80%;
    }
    .downloadButton {
      padding: 6px 15px !important;
      font-size: 14px !important;
    }
    .myLinks a {
      font-size: 18px;
      padding-left: 8px;
    }
  }
</style>