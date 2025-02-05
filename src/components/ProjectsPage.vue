<template>

    <div class="projects" v-if="!showMenu">
        <div class="theProjects d-flex flex-row align-center justify-center">
            <div class="myProjects" v-for="(item,index) in projects" :key="index">
                <div class="container d-flex flex-column">
                     <div class="frontEnd">Frontend
                        <h2>{{ item.number }}</h2>
                     </div>
                     <h3>{{ item.title }}</h3>
                     <div class="languages">
                        <v-icon class="iconLanguages" v-for="(icon,index) in item.icons" :key="index">
                          {{ icon }}</v-icon>
                     </div>
                     <p>{{ item.description }}</p>
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
            ]
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

  inject : ['showMenu'],
  methods: {
    getMarginTop(text){
        const length = text.length
        // return length === 95 || length === 85 ? '2.3vh ': '-1.5vh'
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
  }
}

@media (max-width:1024px){
  .projects{
    overflow-x: hidden;
    overflow-y: auto;
    width:100%;
    ;
    padding-top: 32vh;
  }

  .myProjects{
            width: 55vh;
            height: 33.5vh;
            border: 1px solid rgb(255, 255, 255);
            border-radius: 10px;
            margin-bottom: -5vh;
            margin-left: -5vh;
  }
  .theProjects{
            width: 95%;
            gap: 8vh;
            margin: -12.5vh 5vh -3vh 7vh;
    }
    .container a{
    color: aqua;
    font-size: 17px;
    text-decoration: none;
    margin-top: -1.5vh;
  }
  .container{
    gap: 1.5vh;
    margin-left: 2vh;
  }
}


@media (max-width:768px){

  /* .number {
    color:rgb(254, 254, 254);
    margin-top: -67vh;
    margin-left: 37vh;
    font-size: 40px;
}
.languages{
  margin-top: -5vh;
} */
  
}


@media (max-width: 450px){
  .myProjects{
            width: 55vh;
            height: 33.5vh;
            border: 1px solid rgb(255, 255, 255);
            border-radius: 10px;
            margin-bottom: -5vh;
            margin-left: -9vh;
  }
}
@media (max-width: 365px){
  .myProjects{
            width: 47vh;
            height: 37vh;
            border: 1px solid rgb(255, 255, 255);
            border-radius: 10px;
            margin-bottom: -5vh;
            margin-left: -9vh;
  }
}
</style>