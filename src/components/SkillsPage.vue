<template>

    <div class="skills" v-if="!showMenu">

    <div class="skillsSection" >


       <div class="development">
        <h3>Development</h3>
        <div class="developmentLang">
            <div class="html"> <span>Html</span></div>
            <div class="html">Css</div>
            <div class="html">Scss</div>
            <div class="html">JavaScript</div>
            <div class="html">Vue</div>
        </div>

        <div class="tools">
        <h3>Tools</h3>
        <div class="toolsLang">
            <div class="html">GitHub</div>
            <div class="html">Visual Studio</div>
            <div class="html">NPM</div>
            <div class="html">Node</div>
        </div>
      
        </div>


      </div>

      </div>

      </div>

</template>


<script>
import ScrollReveal from 'scrollreveal';

export default {
    data() {
      return {
        coreShow: true,
        advancedShow: false,
        htmlLang: false,
        cssLang: false,
        jsLang: false,
        github: false,
        vue: false,
        vuetify: false,
      }
    },
    methods: {
      core(){
         this.coreShow= true
         this.advancedShow= false
      },
      advanced(){
         this.coreShow= false
         this.advancedShow= true
      }
    },
    inject: ['showMenu'],

    
  mounted() {
    /****scroll reveal*****/   

  ScrollReveal().reveal(".skillsSection", {
      origin: "none",
      distance: "0px",
      duration: "800",
      easing: "ease-in-out",
      opacity: 0,
    }
  ) 


  },

}
</script>


<style lang="css">
    .skills{
        width:100%;
        height: 100vh;
        pointer-events: auto;
        scroll-behavior: smooth;
        margin-left: -50vh;
    }
    .skillsSection{
      align-items: center;
      display:flex;
      flex-direction: column;
    }
    .development{
      display:flex;
      flex-direction: column;
      text-transform: uppercase;
    }
    .development h3{
      color:rgb(203, 190, 203);
      font-size: 25px;
      font-weight: 700;
      margin-bottom: 4vh;
    }
    .developmentLang{
      display: flex;
      flex-direction: row;
      align-items: center;
      gap: 2vh
    }
      
    .html{
      padding: 12px 18px;
      border: 1px solid transparent;
      border-radius: 7px;
      color:rgb(94, 236, 236);
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0.52) 70%, rgba(0, 0, 0, 0.539) 30%);
    }
    .tools{
      display:flex;
      flex-direction: column;
      margin-top: 10vh;
      text-transform: uppercase;
    }
    .tools h3{
      color:rgb(203, 190, 203);
      font-size: 25px;
      font-weight: 700;
      margin-bottom: 4vh;
    }
    .toolsLang{
      display: flex;
      flex-direction: row;
      align-items: center;
      gap: 2vh
    }
    /* .oneSkills{
    display: flex;
    flex-direction: column;
    padding-left: 2.6vh;
  }
  .twoSkills{
    gap: 15px;
    padding-left: 1vh;

  }
  .twoSkills a{
    text-decoration: none;
    border: 1px solid white;
    border-radius: 10px;
    padding: 18px 5px ;
    font-weight: 600;
    text-align: center;
    width: 58vh;
    font-size: 18px;
    transition: 0.2s ease

  }
  .twoSkills{
    margin-right: 34vh;
    margin-top: -1vh;
    cursor: pointer;
  }
   .html{
    width: 26vh;
    height: 26vh;
    border-radius: 10px;
    background-color: rgba(155, 149, 149, 0.083);
  }
  .iconLang{
    color: aliceblue;
    font-size: 15vh;
    padding: 12vh 13vh;
    cursor: pointer;
    transition: 0.2s ease;
  }
  .html:hover .iconLang{
    color: aqua;
  }

  .threeSkills a{
    text-decoration: none;
    border: 1px solid transparent;
    border-radius: 10px;
    padding: 18px 5px ;
    font-weight: 600;
    text-align: center;
    width: 58vh;
    font-size: 18px;
    cursor: pointer;
    transition: 0.2s ease

  }
  .threeSkills{
    margin-right: 34vh;
    margin-top: -1vh;
  }
  .firstLang{
    border: 1px solid transparent;
    background: white;
    border-radius: 4px;
    width: 13vh;
    height: 5vh;
    
    top: 53.2%;
    left: 54.7%;
    text-align: center;
  }
  .secondLang{
    border: 1px solid transparent;
    background: white;
    border-radius: 4px;
    width: 13vh;
    height: 5vh;
    
    top: 53.2%;
    left: 68.1%;
    text-align: center;
  }
  .thirdLang{
    border: 1px solid transparent;
    background: white;
    border-radius: 4px;
    width: 15vh;
    height: 5vh;
    
    top: 53.2%;
    left: 81%;
    text-align: center;
  }


  .firstLangOne{
    border: 1px solid transparent;
    background: white;
    border-radius: 4px;
    width: 13vh;
    height: 5vh;
    
    top: 52.8%;
    left: 54.2%;
    text-align: center;
  }
  .secondLangOne{
    border: 1px solid transparent;
    background: white;
    border-radius: 4px;
    width: 13vh;
    height: 5vh;
    
    top: 53%;
    left: 67.6%;
    text-align: center;
  }
  .thirdLangOne{
    border: 1px solid transparent;
    background: white;
    border-radius: 4px;
    width: 15vh;
    height: 5vh;
    
    top: 53%;
    left: 80.7%;
    text-align: center;
  }
 */

  @media (max-width:1200px){
    .oneSkills{
    display: flex;
    flex-direction: column;
    padding-left: 0vh;
  }
  .firstLang{
    
    left: 59.2%;
  }
  .secondLang{
    
    left: 74%;
  }
  .thirdLang{
    
    left: 88.1%;
  }
  .firstLangOne{
    
    left: 58.6%;
  }
  .secondLangOne{
    
    left: 73.3%;
  }
  .thirdLangOne{
    
    left: 87.5%;
  }
  .skills{
    overflow-x: hidden;
    overflow-y: hidden;
  }

  }

  @media (max-width:1024px){
    .skills{
        width:100%;
        height: 100vh;
        
        margin: 0;
        padding-top: 32vh;
        overflow-x: hidden;
        overflow-y: hidden;
    }
    .twoSkills{
    margin-right: 10vh;
  }
  .twoSkills a{
    border: 1px solid white;
    padding: 10px 3px ;
    font-weight: 600;
    width: 50vh;
    font-size: 18px;

  }
  .oneSkills p{
    font-size: 15px;
    width: 80% !important
  }
  .html{
    width: 23vh;
    height: 23vh;
    border-radius: 10px;
    background-color: rgba(155, 149, 149, 0.083);
  }
  .iconLang{
    font-size: 12vh;
    padding: 12vh 12vh;
  }
  .firstLang{
    
    left: 52.9%;
  }
  .secondLang{
    
    left: 68.5%;
  }
  .thirdLang{
    
    left: 83.5%;
  }
  .firstLangOne{
    
    left: 49.7%;
  }
  .secondLangOne{
    
    left: 65.2%;
  }
  .thirdLangOne{
    
    left: 80.3%;
  }

  }


  @media (max-width:991px){
    .skills{
      overflow-x: hidden;
      overflow-y: hidden;
    }
    .twoSkills{
    margin-right: 13vh;
  }
  .firstLang{
    
    left: 53.7%;
  }
  .secondLang{
    
    left: 69.8%;
  }
  .thirdLang{
    
    left: 85.3%;
  }
  .firstLangOne{
    
    left: 53.2%;
  }
  .secondLangOne{
    
    left: 69.4%;
  }
  .thirdLangOne{
    
    left: 84.7%;
  }

  }


  @media (max-width:768px){
    .skills{
        width:100%;
        min-height: 100vh;
        
        padding-top: 32vh;
        overflow: hidden;
        overflow-x: hidden;
        overflow-y: auto;
    }
    .oneSkills{
    
    top: 26%;
    left: 20%;
    /* display: none */
  }
  .oneSkills h1{
    margin-bottom: -2vh;
    margin-left: 6vh;
  }
  .oneSkills p{
    position: relative;
    margin-bottom: -17vh;
    left: -16%;
    font-size: 16px;  
    padding: 0px 25px 0px 25px;  
    text-align: center;
  }
  .oneSkills .linkOne{
    margin-top: 15vh;
    margin-left: -5.5vh;
  }
  .oneSkills .linkTwo{
    margin-left: -5.5vh;
  }
  #secondSection h1{
    display: none;
  }
  #secondSection p{
    display: none;
  }
  .languages{
    margin-left: 25vh;
    padding-top: 36vh;
  }
  .html{
    width: 24vh;
    height: 20vh;
  }
  .iconLang{
    margin-top: -2vh;
  }
  .firstLang{
    margin-top: 19.3vh;
    margin-left: -38.5vh;
  }
  .secondLang{
    margin-top: 19.3vh;
    margin-left: -31vh;
  }
  .thirdLang{
    margin-top: 19.3vh;
    margin-left: -24.5vh;
  }
  .firstLangOne{
    margin-top: 19.3vh;
    margin-left: -38.5vh;
  }
  .secondLangOne{
    margin-top: 19.3vh;
    margin-left: -31.8vh;
  }
  .thirdLangOne{
    margin-top: 19.3vh;
    margin-left: -25vh;
  }

  
  }


  @media (max-width:617px){
    .skills{
        width:100%;
        min-height: 100vh;
        
        padding-top: 32vh;
        overflow: hidden;
        overflow-x: hidden;
        overflow-y: auto;
    } 
    .oneSkills{
    
    top: 26%;
    left: 20%;
    /* display: none */
  }
  .oneSkills h1{
    margin-bottom: -2vh;
    margin-left: -1vh;
  }
  .oneSkills p{
    position: relative;
    margin-bottom: -17vh;
    left: -18%;
    font-size: 16px;  
    padding: 0px 10px 0px 10px;  
    text-align: center;
  }
  .oneSkills .linkOne{
    margin-top: 15vh;
    margin-left: -12vh;
  }
  .oneSkills .linkTwo{
    margin-left: -12vh;
  }
  .languages{
    margin-left: 13vh;
  }
  .firstLang{
    margin-top: 19.3vh;
    margin-left: -36.7vh;
  }
  .secondLang{
    margin-top: 19.3vh;
    margin-left: -25vh;
  }
  .thirdLang{
    margin-top: 19.3vh;
    margin-left: -14.7vh;
  }
  .firstLangOne{
    margin-top: 19.3vh;
    margin-left: -37vh;
  }
  .secondLangOne{
    margin-top: 19.3vh;
    margin-left: -26vh;
  }
  .thirdLangOne{
    margin-top: 19.3vh;
    margin-left: -15vh;
  }
  }


  @media (max-width:450px){
    .skills{
        width:100%;
        min-height: 100vh;
        
        padding-top: 32vh;
        overflow: hidden;
        overflow-x: hidden;
        overflow-y: auto;
    } 
    .oneSkills{
    
    top: 26%;
    left: 20%;
    /* display: none */
  }
  .oneSkills h1{
    margin-bottom: -2vh;
    margin-left: -9vh;
  }
  .oneSkills p{
    
    top: 20%;
    left: -27%;
    padding: 0px 0px 0px 0px;
    margin: auto;
    text-align: center;
    font-weight: 900;
    font-size: 16px;
  }
  .oneSkills .linkOne{
    margin-top: 18vh;
    margin-left: -21vh;
  }
  .oneSkills .linkTwo{
    margin-left: -21vh;
    margin-top: 0vh;
  }
  .html{
    width: 20vh;
    height: 16vh;
    margin-top: 5vh;

  }
  .languages{
    margin-left: 3.4vh;
  }
  .iconLang{
    font-size: 10vh;
    padding: 10vh 3vh 3vh 10vh;
  }
  .firstLang{
    margin-top: 24vh;
    margin-left: -33.7vh;
  }
  .secondLang{
    margin-top: 24vh;
    margin-left: -21.3vh;
  }
  .thirdLang{
    margin-top: 24vh;
    margin-left: -10.3vh;
  }
  .firstLangOne{
    margin-top: 24vh;
    margin-left: -34vh;
  }
  .secondLangOne{
    margin-top: 24vh;
    margin-left: -22.4vh;
  }
  .thirdLangOne{
    margin-top: 24vh;
    margin-left: -11vh;
  }
  }


  @media (max-width:365px){
    .skills{
        width:100%;
        min-height: 100vh;
        
        padding-top: 32vh;
        overflow: hidden;
        overflow-x: hidden;
        overflow-y: auto;
    } 
    .oneSkills{
    
    top: 26%;
    left: 10%;
    /* display: none */
  }
  .oneSkills a{
    width: 44vh;
    padding: 9px 0 9px 0;
  }
  .oneSkills .linkOne{
    margin-top: 21vh;
    margin-left: -17.7vh;
  }
  .oneSkills .linkTwo{
    margin-left: -17.7vh;
    margin-top: 0vh;
  }
  .oneSkills p{
    
    top: 17%;
    left: -27%;
    padding: 8px 0px 0px 0px;
    margin: auto;
    text-align: center;
    font-weight: 900;
    font-size: 15px;
    line-height: 28px;
  }
  .html{
    width: 16.5vh;
    height: 14vh;
    margin-top: 8vh;
  }
  .languages{
    margin-left: 1.7vh;
    gap: 1vh;
  }
  .iconLang{
    font-size: 9vh;
    padding: 9.3vh 0vh 0vh 8vh;
  }
  
  .firstLang{
    margin-top: 26vh;
    margin-left: -28vh;
    width: 11vh;
    height: 4.3vh;
  }
  .secondLang{
    margin-top: 26vh;
    margin-left: -17.5vh;
    width: 11vh;
    height: 4.3vh;
  }
  .thirdLang{
    margin-top: 26.5vh;
    margin-left: -7.2vh;
    width: 13vh;
    height: 4.5vh;
    font-size: 14px;
    padding-top: 3px;
    text-align: center;
    font-weight: 900;
  }
  .firstLangOne{
    margin-top: 27.3vh;
    margin-left: -28.4vh;
    width: 11vh;
    height: 4.3vh;
  }
  .secondLangOne{
    margin-top: 27vh;
    margin-left: -17.7vh;
    width: 11vh;
    height: 4.3vh;
  }
  .thirdLangOne{
    margin-top: 26.3vh;
    margin-left: -7.8vh;
    width: 13vh;
    font-size: 14px;
    padding-top: 3px;
    text-align: center;
    font-weight: 900;
  }
  }

  @media (max-width:320px){
    .oneSkills{
    
    top: 26%;
    left: 4%;
  }
  .html{
    width: 14.5vh;
    height: 13vh;
    margin-top: 8vh;
  }
  .languages{
    margin-left: 0.7vh;
    gap: 0.5vh;
  }
  .iconLang{
    font-size: 7vh;
    padding: 9vh 0.5vh 0.3vh 7.3vh;
  }
  .firstLang{
    margin-top: 26vh;
    margin-left: -25.6vh;
    width: 11vh;
    height: 4.3vh;
  }
  .secondLang{
    margin-top: 26vh;
    margin-left: -15.7vh;
    width: 11vh;
    height: 4.3vh;
  }
  .thirdLang{
    margin-top: 26.5vh;
    margin-left: -6.2vh;
    width: 12vh;
    height: 4.5vh;
    font-size: 13px;
    padding-top: 3px;
    text-align: center;
    font-weight: 900;
  }
  .firstLangOne{
    margin-top: 27.3vh;
    margin-left: -26.4vh;
    width: 11vh;
    height: 4.3vh;
  }
  .secondLangOne{
    margin-top: 27vh;
    margin-left: -16.4vh;
    width: 11vh;
    height: 4.3vh;
  }
  .thirdLangOne{
    margin-top: 26.3vh;
    margin-left: -7vh;
    width: 12vh;
    font-size: 13px;
    padding-top: 3px;
    text-align: center;
    font-weight: 900;
  }
  }
</style>