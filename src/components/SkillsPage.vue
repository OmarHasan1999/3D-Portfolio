<template>

    <div class="skills">

    <div class="skills-section" >

      <div class="skill-group">
        <h3>Development</h3>
        <div class="skill-tags">
          <div class="skill-tag">
            <img alt="HTML icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" />
            <span>HTML</span>
          </div>
          <div class="skill-tag">
            <img alt="CSS icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" />
            <span>CSS</span>
          </div>
          <div class="skill-tag">
            <img alt="SCSS icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/sass/sass-original.svg" />
            <span>SCSS</span>
          </div>
          <div class="skill-tag">
            <img alt="JavaScript icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" />
            <span>JavaScript</span>
          </div>
          <div class="skill-tag">
            <img alt="Vue icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg" />
            <span>Vue</span>
          </div>
        </div>
        </div>

         <div class="skill-group">
        <h3>Tools</h3>
        <div class="skill-tags">
          <div class="skill-tag">
            <img alt="GitHub icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" style="filter: invert(1);" />
            <span>GitHub</span>
          </div>
          <div class="skill-tag">
            <img alt="VS Code icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" />
            <span>VS Code</span>
          </div>
          <div class="skill-tag">
            <img alt="NPM icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/npm/npm-original-wordmark.svg" />
            <span>NPM</span>
          </div>
          <div class="skill-tag">
            <img alt="Node.js icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" />
            <span>Node</span>
          </div>
        </div>
      </div>

      <div class="skill-group">
        <h3>Design</h3>
        <div class="skill-tags">
          <div class="skill-tag">
            <img alt="Figma icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" />
            <span>Figma</span>
          </div>
        </div>
      </div>
      
        </div>

      </div>
</template>
<script>
export default {
    data() {
      return {
        
      }
    },
    methods: {
      
    },

    
  mounted() {
    /****scroll reveal*****/   
  },

}
</script>


<style lang="css">
    .skills{
        width:100%;
        height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center; 
        padding-bottom: 18vw;
        padding-right: 12vw;
    }
  
    .skills-section{
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      gap: 3vh;
      padding: 0 16px;
    }
    .skill-group {
    display: flex;
    flex-direction: column;
    gap: 2vh;
}
    
    .skill-group h3 {
    color: rgb(203, 190, 203);
    font-size: 22px;
    font-weight: 700;
}

    .skill-tags {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;      
    gap: 14px;
}

    .skill-tag {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 8px;
    padding: 14px 20px;
    border: 1px solid rgba(0, 255, 255, 0.15);
    border-radius: 10px;
    background: linear-gradient(to bottom, rgba(0,0,0,0.52), rgba(0,0,0,0.54));
    transition: border-color 0.2s ease, transform 0.2s ease;
    cursor: default;
    min-width: 70px;
}

.skill-tag:hover {
    border-color: rgba(0, 255, 255, 0.6);  
    transform: translateY(-3px);
}

.skill-tag img {
    width: 36px;
    height: 36px;
    object-fit: contain;
}

.skill-tag span {
    font-size: 14px;
    color: rgb(94, 236, 236);
    text-align: center;
}

/* Responsive */
@media (max-width: 1000px) {
    .skills {
        padding-right: 25vw;
    }
}
@media (max-width: 800px) {
    .skills {
        padding-right: 33vw;
        padding-bottom: 25vw;
    }
}
@media (max-width: 767px) {
    .skills {
        padding-right: 23vw;
        padding-bottom: 35vw;
    }
    
}
@media (max-width: 665px) {
    .skills {
        padding-right: 18vw;
        padding-bottom: 38vw;
    }
    
}
@media (max-width: 625px) {
  .skills {
        padding-right: 20vw;
        padding-bottom: 45vw;
    }
    .skill-tag {
        min-width: 60px;
        padding: 10px 14px;
    }
    .skill-tag img {
        width: 28px;
        height: 28px;
    }
    .skill-tag span {
        font-size: 12px;
    }
}
@media (max-width: 500px) {
  .skills {
        padding-right: 16vw;
        padding-bottom: 54vw;
    }
}
@media (max-width: 450px) {
  .skills {
        padding-right: 12vw;
        padding-bottom: 60vw;
    }
  .skills-section{
        padding-right: -7vw;
        margin-left: -7vw;
  }
  .skill-tags {
    gap: 7px;
}
}
@media (max-width: 400px) {
  .skills {
        padding-bottom: 78vw;
    }
  .skills-section{
        margin-left: -6vw;
  }
  .skill-tags {
    gap: 3px;
}
}
</style>