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

        <div class="design">
        <h3>Design</h3>
        <div class="designTool">
            <span>Figma</span>
        </div>
        </div>

      
        </div>

      </div>

      <div class="img">
        <img src="../assets/code-1970468_1280.png">
      </div>


      </div>

      </div>

</template>


<script>
// import ScrollReveal from 'scrollreveal';

export default {
    data() {
      return {
        
      }
    },
    methods: {
      
    },
    inject: ['showMenu'],

    
  mounted() {
    /****scroll reveal*****/   
  },

}
</script>


<style lang="css">
    .skills{
        width:100%;
        height: 100vh;
        pointer-events: auto;
        scroll-behavior: smooth;
        margin-left: -20vh;
        overflow: hidden;

    }
  
    .skillsSection{
      align-items: center;
      display:flex;
      flex-direction: column;
    }
    .development{
      display:flex;
      flex-direction: column;
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
      padding: 12px 25px;
      border: 1px solid transparent;
      border-radius: 7px;
      font-size: 18px;
      color:rgb(94, 236, 236);
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0.52) 70%, rgba(0, 0, 0, 0.539) 30%);
    }
    .tools{
      display:flex;
      flex-direction: column;
      margin-top: 6vh;
    }
     .img img{
      width: 90vh;
      margin-left: 30vh;
      margin-top: -60vh;
      opacity: 0.09; 
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

    .design{
      display:flex;
      flex-direction: column;
      margin-top: 6vh;
    }
    .designTool span{
      padding: 12px 25px;
      font-size: 18px;
      border: 1px solid transparent;
      border-radius: 7px;
      color:rgb(94, 236, 236);
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0.52) 70%, rgba(0, 0, 0, 0.539) 30%);
    }

  @media (max-width:1200px){
    .oneSkills{
    display: flex;
    flex-direction: column;
    padding-left: 0vh;
  }
  .skills{
    overflow-x: hidden;
    overflow-y: hidden;
  }

  }

  @media (max-width:1024px){
    

  }


  @media (max-width:991px){
   
  }


  @media (max-width:768px){
    .skills{
    margin-left: -5vh !important;
    margin-top: -5vh !important;
  }
  h3{
    margin-left: 0vh !important;
  }
  .img img{
      margin-left: 17vh;
    }
    .html{
      padding: 8px 21px;
      font-size: 17px;
    }
    .designTool span{
      font-size: 16px;
      padding: 8px 21px;
    }
  }


  @media (max-width:617px){
    .skills{
    margin-top: 1vh !important;
  }
    .html{
      padding: 5px 16px;
      font-size: 15px;
    }
    .designTool span{
      font-size: 16px !important;
      padding: 8px 19px;

    }
    .img img{
      margin-left: 13vh;
    }
    .skillsSection h3{
      font-size: 20px;
      font-weight: 700;
    }
  }

  @media (max-width:450px){
    .skills{
    margin-left: -2.5vh !important;
  }
  .html{
      padding: 3px 12px;
      font-size: 14px;
      margin-right: -1vh;
    }
    .designTool span{
      font-size: 16px !important;
      padding: 8px 19px;
    }
    .img img{
      margin-left: 1vh;
      width: 80vh;
    }
  }

  @media (max-width:375px){
    .skillsSection{
      margin-left: -2vh;
      
    }
    .img img{
      margin-left: 0.7vh;
      width: 55vh;
      height: 50vh;
    }
    .html{
      padding: 3px 10px;
      font-size: 12px;
      margin-right: -1vh;
    }
    .designTool span{
      font-size: 12px !important;
      padding: 5px 10px;
    }
  }

  @media (max-width:320px){
    .html{
      padding: 3px 8px;
      font-size: 11px;
      margin-right: -1vh;
    }
    .designTool span{
      font-size: 11px !important;
      padding: 5px 8px;
    }
    .skillsSection{
      margin-left: -6vh;
    }
    .skillsSection h3{
      font-size: 18px !important
    }
    .developmentLang, .toolsLang{
      gap: 1.6vh
    }
  }
</style>