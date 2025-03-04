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
    padding-top: 44rem;
    padding-bottom: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    /* z-index: 1000000; */
  }

  .links {
    margin-left: -4vh;
    display: flex;
    gap: 15.5vh;
    flex-direction: column;
    align-items: center;
  }

  .links a {
    text-decoration: none;
    color: aliceblue;
    margin-left: 25px;
    font-size: 20px;
    font-weight: 600;
    transition: 0.2s ease;
    display: flex;
    align-items: center;
    rotate: -90deg;
    pointer-events: auto;
    padding: 0;
    display: inline-block;
  }

  .links .routers:hover {
  color: aqua;
  cursor: pointer;
  pointer-events: auto;
}

  .links a.router-link-exact-active {
    color: aqua;
  }


.links a.router-link-exact-active {
  color: aqua;
    }

    /* responsive */
    @media (min-width:2560px){
      .app-bar {
        padding-bottom: 10rem;
    }
  }
    @media (max-width:1200px){
      .app-bar {
        padding-bottom: 8rem;
    }
  }
  @media (max-width:1024px){
      .app-bar {
        padding-bottom: 9rem;
    }
  }
  @media (max-width:768px){
      .app-bar {
        padding-left: -2rem !important;
    }
    .links a{
      font-size: 17px !important;

    }
  }
  @media (max-width:617px){
    .app-bar {
        margin-left: -0.5rem !important;
    }
  }
  @media (max-width:320px){
    .app-bar {
        margin-left: -0.9rem !important;
    }
  }
</style> 