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
import ScrollReveal from 'scrollreveal';

export default {
   inject: ['showMenu', 'showLinks', 'scrollDown'],

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
    hideMenu(){
      if(this.showMenu){
        this.showLinks()
      }
    },
   },

   computed: {
    isScroll() {
      return this.scrollDown?.value;  // Use the global scroll state
    }
  },

   mounted() {
    /****scroll reveal*****/   
  ScrollReveal().reveal(".linksTwo", {
      origin: "top",
      distance: "50px",
      duration: "1000",
      easing: "ease-in-out"
    }
  )
  }
}
</script>

<style lang="css">
.disabled {
  pointer-events: none;  /* Prevents clicks */
  opacity: 0.5; /* Makes it look disabled */
  cursor: default;
}
.headerPage {
    width: 100%;
  }

  .app-bar {
    padding-top: 44rem;
    padding-bottom: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    z-index: 1000000;
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

  .linksTwo a.router-link-exact-active {
    color: aqua;
  }

  .menuIcon {
    display: none;
    cursor: pointer;
    font-size: 30px;
    margin-left: 50vh;
    color: aliceblue;
  }

  .linksTwo {
    display: none;
    scroll-behavior: smooth;
  }


  .menuIcon {
    display: none;
    cursor: pointer;
    font-size: 30px;
    margin-left: 50vh;
    color: aliceblue;
  }

  .linksTwo {
    display: none;
    scroll-behavior: smooth;
  }

.links a.router-link-exact-active {
  color: aqua;
    }
.linksTwo a.router-link-exact-active {
  color: aqua;
    }

  .menuIcon{
    display: none;
    cursor: pointer;
    font-size: 30px;
    margin-left: 50vh;
    color: aliceblue;
  }
  .linksTwo{
    display: none;
    scroll-behavior: smooth;
  }


  @media (max-width:1200px){
    
.headerPage {
  width: 100%;
}

.app-bar {
  padding-top: 1.4rem;
  padding-bottom: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  z-index: 1000000;
}

.logo {
  margin-left: 0.7rem;
  padding-left: 3.75rem;
  color: aliceblue;
  font-size: 27px;
}

.logo span.highlight {
  color: aqua;
}

.links {
  margin-left: 70vh;
  display: flex;
  align-items: center;
}

.links .routers {
  text-decoration: none;
  color: aliceblue;
  padding-left: 45px;
  font-size: 17px;
  font-weight: 600;
  transition: 0.2s ease;
  display: flex;
  align-items: center;
  
}

.links .routers .mdi {
  font-size: 20px;
  margin-right: 5px;
}

.links .routers:hover{
        color: aqua;
        
    }
.links a.router-link-exact-active {
  color: aqua;
    }

  .menuIcon{
    display: none;
    cursor: pointer;
    font-size: 30px;
    margin-left: 50vh;
    color: aliceblue;
  }
  }


  @media (max-width:1024px){
   
    .links {
      margin-left: 37vh;
      display: flex;
      align-items: center;
}
.links .routers {
  text-decoration: none;
  color: aliceblue;
  padding-left: 35px;
  font-size: 16px;
  font-weight: 600;
  transition: 0.2s ease;
  display: flex;
  align-items: center;
  
}
  }

  @media (max-width:991px){

    .app-bar {
  padding-top: 1.4rem;
  padding-bottom: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  z-index: 1000000;
  width: 100%;
}
    .headerPage {
      width: 100%;
}
    .logo {
            margin-left: 18vh;
            padding-left: 0;
            font-size: 30px;
            
}
.links {
      margin-left:10vh;
      margin-right:10vh;
      display: flex;
      align-items: center;
}

  .links .routers {
    padding: 18px 18px;
    text-align: center;
    width: 100%;
    transition: 0.2s ease;
    font-size: 18px;
    padding-left: 35px;

  }
  }
   

  @media (max-width:768px){
    .logo {
            margin-left: 10vh;
            padding-left: 0;
            
}
.menuIcon{
  display: block;
  transition: 0.2s ease;
  margin-left: 20vh;
  margin-right: 10vh;
}
.links {
  display: none;
}
.linksTwo {
    display: flex;
    transition: 0.2s ease;
    align-items: center;
    text-align: center;
    top: 100px;
    left: 40%;
    width: 100%;
    padding: 30px 0;
    flex-direction: column;
    transition: 0.2s ease;

  }


  .linksTwo .routers {
    text-decoration: none;
    color: aliceblue;
    padding-left: 55px;
    font-size: 30px;
    font-weight: 600;
    transition: 0.2s ease;
    display: flex;
    align-items: center;
    padding: 22px 0px;
    text-align: center;
    width: 100%;
    transition: 0.2s ease;

  }
  }


  @media (max-width:617px){
    .links {
  display: none;
}
    .menuIcon{
  display: block;
  transition: 0.2s ease;
  margin-left: 20vh;
  margin-right: 5vh;
}
    .logo {
            margin-left: 8vh;
            padding-left: 0;           
}
.links{
  left: 33%;
}
  }

  @media (max-width:450px){
    .logo {
            margin-left: 7vh;
            padding-left: 0;           
}
.menuIcon{
  display: block;
  transition: 0.2s ease;
  margin-left: 12vh;
  margin-right: 3vh;
}
.linksTwo{
  left: 37%;
}
  }


  @media (max-width:365px){
    .links {
  display: none;
}
    .logo {
            margin-left: 4vh;
            padding-left: 0;  
            font-size: 26px;         
}
.menuIcon{
    font-size: 23px;
    margin-left: 12vh;
    margin-right: 3vh;
  }
  .linksTwo{
  left: 33%;
}
  }
  @media (max-width:320px){
    .logo {
            margin-left: 4vh;
            padding-left: 0;  
            font-size: 26px;         
}
.menuIcon{
    font-size: 25px;
    margin-left: 5vh;
    margin-right: 3vh;
  }
  .linksTwo{
  left: 28%;
}
  }

</style> 