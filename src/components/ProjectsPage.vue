<template>

    <div class="projects">
        <div class="theProjects d-flex flex-row align-center justify-center">
            <div class="myProjects" v-for="(item,i) in projects" :key="i">
                <div class="container d-flex flex-column">
                     <div class="frontEnd">
                      <span>Frontend</span> 
                        <h2>{{ item.number }}</h2>
                     </div>
                     <h3>{{ item.title }}</h3>
                     <div class="languages">
                        <v-icon class="iconLanguages" v-for="(icon,i) in item.icons" :key="i">
                          {{ icon }}</v-icon>
                     </div>
                     <p ref="desc">{{ item.description }}</p>
                     <a :style="{marginTop: getMarginTop(item.description)}" :href="item.link" target="blank">Github link</a>
                </div>
            </div>

        </div>

    </div>
</template>


<script>
// import ScrollReveal from 'scrollreveal';

export default {
    data() {
        return {
            projects : [
                {
                    title : "Mobile-Shop",
                    description : "A commercial for phone sales,offering an intuitive shopping experience for mobile enthusiasts",
                    link: "https://github.com/OmarHasan1999/Mobile-Shop",
                    number: "01",
                    icons:  ["mdi-language-html5", "mdi-language-css3", "mdi-vuejs"]
                      
                    
                },
                {
                    title : "vue-course",
                    description : "A complete Vue learning platform, Options API, Composition API, Vuex, Vuetify, and Pinia",
                    link: "https://github.com/OmarHasan1999/vue-course",
                    number: "02",
                    icons: ["mdi-vuejs", "mdi-vuetify", "mdi-language-javascript"]
                    
                },
                {
                    title : "To-do-list",
                    description : "A sleek Vue task manager,enabling effortless task organization and tracking",
                    link: "https://github.com/OmarHasan1999/ToDoListApp",
                    number: "03",
                    icons: ["mdi-language-html5", "mdi-language-css3", "mdi-language-javascript"]
                    
                },
                {
                    title : "Library-website",
                    description : "online library with a vast collection, offering detailed book info and easy downloads",
                    link: "https://github.com/OmarHasan1999/Library-website",
                    number: "04",
                    icons: ["mdi-language-html5", "mdi-language-css3", "mdi-vuejs", "mdi-code-json"]
                    
                },
                {
                    title : "Watches-Market",
                    description : "A dynamic e-commerce site for watches,featuring engaging shopping and secure transactions.",
                    link: "https://github.com/OmarHasan1999/Watches-Market",
                    number: "05",
                    icons: ["mdi-language-html5", "mdi-language-css3", "mdi-language-javascript", "mdi-vuejs"]
                    
                }
            ],
        }
        
    },
  mounted() {
    /****scroll reveal*****/   
//     ScrollReveal().reveal(".theProjects", {
//       origin: "none",
//       distance: "0px",
//       opacity:0,
//       duration: "500",
//       easing: "ease-in-out",
//     }
//   )
  },

  // inject : ['showMenu'],
  methods: {
    getMarginTop(text){
        const length = text.length
        if(length === 85){
            return '2vh'
        }else if(length === 75){
            return '2vh'
        }else{
            return '-1.5vh'
        }
        
    }
  },

}
</script>


<style lang="css">
    .projects{
        width:100%;
        height: 100vh;
        ;
        padding-top: 32vh;
        scroll-behavior: smooth;
        overflow: hidden;
    }
    .theProjects{
            flex-wrap: wrap;
            width: 95%;
            gap: 10vh;
            margin: -12.5vh 5vh -3vh 7vh;
    }
    .myProjects{
            width: 55vh;
            height: 36vh;
            border: 1px solid rgb(255, 255, 255);
            border-radius: 10px;
            margin-bottom: -5vh;
  }
  .container{
    gap: 2vh;
    margin-left: 2vh;
    pointer-events: auto;
  }
  .container a{
    color: aqua;
    font-size: 17px;
    text-decoration: none;
    font-weight: 600;
    display: inline-block;
    padding:0;
    align-self: flex-start
  }
  .container p{
    color: rgba(255, 255, 255, 0.737);
    width: 90%;
    font-size: 14px;
    margin-top: -1vh;
  }
  .container h3{
    color: #e2eef0;
    font-size: 17px;
    font-weight: 400;
  }
  .frontEnd{
    border: 1px solid white;
    width: 12vh;
    height: 4.5vh;
    font-size: 15px;
    font-weight: 700;
    color: rgba(0, 0, 0, 0.768);
    border-radius: 5px;
    background-color: #e2eef0;
    border-color: #e2eef0;
    margin-top: 1.7vh;
    text-align: center;
  }
  .frontEnd h2{
    display: flex;
    align-items: center;
    color:rgb(254, 254, 254);
    margin-left: 35vh;
    font-size: 40px;
    -webkit-animation: glow 2s ease-in-out infinite alternate;
    -moz-animation: glow 2s ease-in-out infinite alternate;
    animation: glow 2s ease-in-out infinite alternate;
  }
  .languages{
    color: #e2eef0;
    font-size: 13px;
  }
  .iconLanguages{
    margin-right: 1.8vh;
  }

@-webkit-keyframes glow {
  from {
    color: #fff;
    text-shadow: 0 0 0px #00fff2, 0 0 5px #00fff2, 0 0 10px #00fff2, 0 0 15px #00fff2, 0 0 23px #00fff2, 0 0 33px #00fff2, 0 0 40px #00fff2, 0 0 80px #00fff2;
  }
  to {
    color: gray;
    text-shadow: 0 0 0px #00fff2, 0 0 10px #00fff2, 0 0 20px #00fff2, 0 0 30px #00fff2, 0 0 40px #00fff2, 0 0 50px #00fff2, 0 0 60px #00fff2, 0 1 70px #00fff2;
  }
}



@media (max-width:1200px){
  .projects{
    overflow-x: hidden;
    overflow-y: hidden;
    scroll-behavior: smooth;
    padding-top: 27vh;
  }
  .container a{
    margin-top: -6.3vh !important;
    margin-left: 35vh;
    font-size: 15px !important;
  } 
  .frontEnd{
    font-size: 13px;
    font-weight: 700;
  }
  .frontEnd h2{
    font-size: 30px;
  }
}

@media (max-width:1024px){
  .theProjects{
    gap: 8vh !important;
    margin-left: 9vh !important;
    margin-top: -5vh !important;
  }
   .myProjects{
            width: 54vh;
            height: 33.5vh;
            border: 1px solid rgb(255, 255, 255);
            border-radius: 10px;
            margin-bottom: -5vh;
            margin-right: -4vh;
  }
    .container a{
    margin-top: -5.5vh !important;
    margin-left: 34vh;
  }
  .container{
    gap: 1.5vh;
    margin-left: 2vh;
  }
}

@media (max-width:991px){
  .container a{
    margin-top: -5.6vh !important;
  }
}

@media (max-width:768px){
  .myProjects{
            width: 47vh;
            height: 25.5vh;
  }
  .theProjects{
    margin-left: 5vh !important;
    margin-top: -12vh !important;
  }
  .container h3{
    font-size: 13px !important;
    font-weight: 500;
    margin-top: 2vh;
  }
  .iconLanguages{
    margin-right: 1.8vh;
    font-size: 15px !important;
    margin-top: -1.1vh;
  }
  .frontEnd{
    display: none;
  }
  .container p{
    color: rgba(255, 255, 255, 0.737);
    width: 90%;
    font-size: 12px;
    margin-top: -1vh;
  }
  .container a{
    margin-top: -5vh !important;
    margin-left: 30vh;
    font-size: 12px !important;
  } 
}


@media (max-width: 450px){
  .theProjects{
    margin-left: 3vh !important;
    margin-top: -11vh !important;
    overflow-x: auto !important;
    scroll-snap-type: x mandatory !important;
    -webkit-overflow-scrolling: touch !important;
    height: 80vh;
  }
  .myProjects{
    scroll-snap-align: center !important;
    flex: 0 0 auto !important;
  }

}

@media (max-width: 320px){
  .myProjects{
            width: 46vh;
            height: 22vh;
  }
  .theProjects{
            flex-wrap: wrap;
            width: 91%;
} 
.container{
  gap: 1vh !important;
  margin-top: -0.7vh !important;
}
.container a{
    margin-top: -4.7vh !important;
    margin-left: 29.3vh;
    font-size: 12px !important;
  } 
}
</style>