<template>
  <!-- header section -->
  <header>
        <div class="headerPage">
            <div class="app-bar">
              <div class="links">
                <a class="routers" href="/" @click.prevent="homePage">
                  Home
                </a>
                <a class="routers" href="/Skills" @click.prevent="skillsPage">
                  Skills
                </a>
                <a class="routers" href="/Projects" @click.prevent="projectsPage">
                  Projects
                </a>
                <a class="routers" href="/Contact" @click.prevent="contactPage">
                  Contact
                </a>
                
              </div>
            </div>
          </div>          
    </header>
</template>


<script>

export default {

   methods: {
    skillsPage(){
        this.$emit('toSkillsPage')
    },
    projectsPage(){
        this.$emit('toProjectsPage')
    },
    contactPage(){
      this.$emit('toContactPage')
    },
    homePage(){
      this.$emit('toHomePage')
    },

}
}
</script>

<style lang="css">
.headerPage {
    width: 100%;
  }

  .app-bar {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    padding: 0%;
    margin: 0%;
  }

  .links {
    margin: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    padding: 0px 7px;
    position: absolute;
    left: 0;
    top: 0;
    gap: 90px;
  }

  .links a {
    text-decoration: none;
    color: aliceblue;
    font-size: 18px;
    font-weight: 600;
    transition: 0.2s ease;
    display: flex;
    align-items: center;
    rotate: -90deg;
    pointer-events: auto;
    padding: 0;
    display: inline-block;
    white-space: nowrap;
  }

  .links .routers:hover {
  color: aqua;
  cursor: pointer;
  pointer-events: auto;
}

  .links a.router-link-exact-active {
    color: aqua;
  }

    /* responsive */
   @media (max-width:500px) {
    .links{
      left: -16px;
    }
    
   }
</style> 