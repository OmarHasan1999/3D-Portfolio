<template>

    <div class="projects">
        <div class="the-projects">
            <div class="my-projects" v-for="(item,i) in projects" :key="i">
                <div class="card-inner">

                    <div class="card-header">
                      <span class="badge">Frontend</span> 
                        <h2 class="project-num">{{ item.number }}</h2>
                    </div>

                    <h3 class="project-title">{{ item.title }}</h3>

                    <div class="languages">
                        <v-icon class="icon-lang" v-for="(icon,i) in item.icons" :key="i" :icon="icon">
                          {{ icon }}
                        </v-icon>
                    </div>

                    <p class="project-desc">{{ item.description }}</p>
                    <a :href="item.link" target="_blank" class="project-link">Github link →</a>
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
                    title : "Library-website",
                    description : "online library with a vast collection, offering detailed book info and easy downloads",
                    link: "https://github.com/OmarHasan1999/Library-website",
                    number: "02",
                    icons: ["mdi-language-html5", "mdi-language-css3", "mdi-vuejs", "mdi-code-json"]
               
                },
                {
                    title : "Watches-Market",
                    description : "A dynamic e-commerce site for watches,featuring engaging shopping and secure transactions.",
                    link: "https://github.com/OmarHasan1999/Watches-Market",
                    number: "03",
                    icons: ["mdi-language-html5", "mdi-language-css3", "mdi-language-javascript", "mdi-vuejs"]
                    
                }
            ],
        }
        
    },
  mounted() {
  },

  methods: {
    
  },

}
</script>


<style lang="css">
    .projects{
        width:100%;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .the-projects{
        display: flex; 
        flex-direction: row;
        align-content: stretch;
        justify-content: center;
        gap: 24px;
        padding:0 24px;
        width: 100%;
        max-width: 1100px;
    }
    .my-projects{
            width: 300px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 12px;
            background: linear-gradient(135deg, rgba(0,0,0,0.45), rgba(0,0,0,0.3));
            backdrop-filter: blur(6px);
            transition: border-color 0.25s ease, transform 0.25s ease;
            pointer-events: auto;
  }
  .my-project:hover {
    border-color: rgba(0, 255, 255, 0.5);
    transform: translateY(-4px);
}
  .card-inner{
    display: flex;
    flex-direction: column;
    padding: 20px;
    gap: 12px;
    height: 100%;
  }

  .card-header {
    display: flex;
    align-items: center;
    justify-content: space-between;  
}
  .badge {
    font-size: 13px;
    font-weight: 700;
    color: rgba(0, 0, 0, 0.8);
    background-color: #e2eef0;
    border-radius: 5px;
    padding: 3px 10px;
}

  .project-num {
    font-size: 36px;
    font-weight: 700;
    color: #fff;
    animation: glow 2s ease-in-out infinite alternate;
}

  .project-title {
    color: #e2eef0;
    font-size: 17px;
    font-weight: 500;
}

  .languages {
    display: flex;
    flex-direction: row;
    gap: 8px;
    color: #e2eef0;
}
  .icon-lang {
    font-size: 20px;
    color: #e2eef0;
}

  .project-desc {
    color: rgba(255, 255, 255, 0.75);
    font-size: 14px;
    line-height: 1.6;
    flex-grow: 1;              
}

  .project-link {
    color: aqua;
    font-size: 15px;
    font-weight: 600;
    text-decoration: none;
    align-self: flex-start;
    transition: opacity 0.2s ease;
}

.project-link:hover {
    opacity: 0.75;
}

  /* Glow animation */
@keyframes glow {
    from {
        color: #fff;
        text-shadow: 0 0 5px #00fff2, 0 0 10px #00fff2, 0 0 20px #00fff2;
    }
    to {
        color: gray;
        text-shadow: 0 0 10px #00fff2, 0 0 25px #00fff2, 0 0 40px #00fff2;
    }
}

/* responsive design */
@media (max-width: 990px) {
    .the-projects {
        gap: 16px;
    }
}

@media (max-width: 800px) {
  .projects{
    padding-top: 6vw;
  }
    .the-projects {
        flex-wrap: wrap;
        align-items: center;
        padding: 0 16px;
    }
    .my-projects {
        width: 100%;
        max-width: 270px;
    }
    .card-inner{
    padding: 16px;
    gap: 8px;
  }
    .project-num {
        font-size: 26px;     
    }

    .project-title {
        font-size: 15px;
    }

    .project-desc {
        font-size: 13px;
    }
}

@media (max-width: 600px) {
  .projects{
    padding-left: 4vw;
  }
    .the-projects {
        gap: 8px;
        padding: 0 20px;

    }
    .my-projects {
        max-width: 100%;
        width: 400px;
    }
    .card-inner{
    padding: 12px;
    gap: 6px;
  }
  .project-desc{
    line-height: 1.4;
  }
}
@media (max-width: 500px) {
  .projects{
    padding-top: 10vw;
    padding-right: 3vw;
  }
    .the-projects {
        gap: 4px;
        padding: 0 12px;
    }
    .my-projects {
        width: 400px;
        max-width: 100%;
    }
    .card-inner{
    padding: 10px;
    gap: 4px;
  }
}
@media (max-width:480px) {
  .projects{
    padding-left: 8vw;
  }
}
@media (max-width: 400px) {
  .projects{
    padding-top: 12vw;
    padding-left: 11vw;
  }
    .the-projects {
        gap: 6px;
        padding: 0 8px;
    }
    .my-projects {
        width: 100%;
        max-width: 100%;
    }
    .card-inner{
    padding: 8px;
    gap: 2px;
  }
}
</style>