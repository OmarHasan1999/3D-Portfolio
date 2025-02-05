<template>
  <div ref="theContainer" class="theContainer">

  <header-page class="headerPage" @toSkillsPage="goSkillsPage" 
  @toProjectsPage="goProjectsPage" @toContactPage="goContactPage" 
  @toHomePage="goHomePage" />

    <home-page class="homePage"/>
  
    <skills-page class="skillsPage"/>

    <projects-page class="projectsPage"/>
  
    <contact-page class="contactPage"/>
  
  </div>
  
</template>

<script>
import * as THREE from 'three'
import gsap from 'gsap'
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader.js';
import { CSS2DRenderer, CSS2DObject } from 'three/examples/jsm/renderers/CSS2DRenderer.js';
import { onMounted, ref } from 'vue';
import HeaderPage from '../components/HeaderPage.vue';
import { nextTick } from 'vue';
import HomePage from '../components/HomePage.vue';
import SkillsPage from '../components/SkillsPage.vue';
import ProjectsPage from '../components/ProjectsPage.vue';
import ContactPage from '../components/ContactPage.vue';

export default {
  components: { HeaderPage, HomePage, SkillsPage, ProjectsPage, ContactPage },
  setup(){
    const theContainer = ref(null);
    const headerObjectRef = ref(null);
    let scene, camera, renderer, labelRender

    const moveCamera = (x, y, z) => {
        gsap.to(camera.position, {
            x,
            y,
            z,
            duration : 3,
        }
    )
}

    const rotateCamera = (x, y, z) => {
        gsap.to(camera.rotation, {
            x,
            y,
            z,
            duration : 3.2,
        })}
  
        const goSkillsPage = () => {
            if(!camera) return
            // moveCamera(10, 13, 2)
            // rotateCamera(0.5, 0 , -0.3)
            moveCamera(-38, 31, -8)
            rotateCamera(-0.6, 0, 0)
            if (headerObjectRef.value) {
                // headerObjectRef.value.position.set(11.2, 20.5, -3.8);
                 headerObjectRef.value.position.set(-38, 25, -39);
    }
    }

        const goProjectsPage = () => {
            if(!camera) return
            moveCamera(-1.8, -0.5, 5)
            rotateCamera(0.2, 0.5 , 0)
            if (headerObjectRef.value) {
                headerObjectRef.value.position.set(-4.3, 2.6, 1);
    }
    }


    const goContactPage = () => {
            if(!camera) return
            moveCamera(-1.8, -11.5, 5)
            rotateCamera(0.2, 0.5 , 0)
            if (headerObjectRef.value) {
                headerObjectRef.value.position.set(-7.3, -4.4, -4);
            
    }
    }

    const goHomePage = () => {
            if(!camera) return
            if(camera.position.y === 0){
              console.log("Home page")
            }else{
              moveCamera(-1.7, 0, 8.7);
              rotateCamera(0, 4.7, 0);
              if (headerObjectRef.value) {
                headerObjectRef.value.position.set(38, 17, 9);
            }
           
    }
    }


    onMounted(() => {
      scene = new THREE.Scene();
      camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);
      camera.position.set(-1.7, 0, 8.7)
      camera.lookAt(1.7, 0, 8.7)
      
      renderer = new THREE.WebGLRenderer({ antialias: true });
      renderer.setSize(window.innerWidth, window.innerHeight);
      theContainer.value.appendChild(renderer.domElement);
      
      // lights
      const ambientLight = new THREE.AmbientLight(0xffffff, 2);
      scene.add(ambientLight);

      const directionalLight = new THREE.DirectionalLight(0xffffff, 5);
      directionalLight.position.set(2,4,5);
      scene.add(directionalLight);

      const light1 = new THREE.PointLight(0xffffff, 2);
      light1.position.set(0, 3, 3);
      scene.add(light1);

      const light2 = new THREE.PointLight(0xffffff, 2);
      light2.position.set(-3, -3, 3);
      scene.add(light2);

      labelRender = new CSS2DRenderer();
      labelRender.setSize(window.innerWidth, window.innerHeight);
      labelRender.domElement.style.position = 'absolute';
      labelRender.domElement.style.pointerEvents = 'none';
      labelRender.domElement.style.top = '0px';
      theContainer.value.appendChild(labelRender.domElement);

      nextTick(() => {
        // add header to the scene
          const header = document.querySelector(".headerPage")
          const headerObject = new CSS2DObject(header);
          headerObject.position.set(38, 17, 8.7);
          scene.add(headerObject);
          headerObjectRef.value = headerObject;

        // add home page to scene
          const home = document.querySelector(".homePage")
          const homeObject = new CSS2DObject(home);
          homeObject.position.set(38, 2.3, 8.7);
          scene.add(homeObject);

        // add skills to scene
          const skillsPage = document.querySelector(".skillsPage")
          const skillsObj = new CSS2DObject(skillsPage)
          skillsObj.position.set(0, -280, -300)
          scene.add(skillsObj)

          // add projects page to scene
          const projectsPage = document.querySelector(".projectsPage")
          const projectsObject = new CSS2DObject(projectsPage);
          projectsObject.position.set(-6.7, 1.6, -4);
          scene.add(projectsObject);
      })

          // add contact to scene
            const contact = document.querySelector(".contactPage")
            const contactObj = new CSS2DObject(contact)
            contactObj.position.set(-6.4,-9.6,-4)
            scene.add(contactObj)
      
      let laptop
      const theObj = new URL("../assets/3d_clipart_-_webdev.glb",import.meta.url)
      const theObjLoad = new GLTFLoader()
      theObjLoad.load(theObj.href,(gltf) => {
        laptop = gltf.scene
        laptop.scale.set(1.2, 1.3, 1.2)
        laptop.position.set(25, -4.9, 22);
        laptop.rotation.y = 4.3
        scene.add(laptop);

})

      let facebook
      const thefacebook = new URL("../assets/3d icon facebook.glb",import.meta.url)
      const theObjLoad_2 = new GLTFLoader()
      theObjLoad_2.load(thefacebook.href,(gltf) => {
        facebook = gltf.scene
        facebook.scale.set(0.54, 0.54, 0.54)
        facebook.position.set(30, -9.6, -1.2)
        facebook.rotation.y = 4.7
        scene.add(facebook);

})

      let github
      const thegithub = new URL("../assets/github.glb",import.meta.url)
      const theObjLoad_3 = new GLTFLoader()
      theObjLoad_3.load(thegithub.href,(gltf) => {
        github = gltf.scene
        github.scale.set(0.54, 0.54, 0.54)
        github.position.set(30, -9.6, 0.1);
        github.rotation.y = 4.7
        scene.add(github);
})

      let linkedin
      const thelinkedin = new URL("../assets/linkedin.glb",import.meta.url)
      const theObjLoad_4 = new GLTFLoader()
      theObjLoad_4.load(thelinkedin.href,(gltf) => {
        linkedin = gltf.scene
        linkedin.scale.set(0.54, 0.54, 0.54)
        linkedin.position.set(30, -9.6, 1.4);
        linkedin.rotation.y = 4.7
        scene.add(linkedin);
})

      let whatsapp
      const thewhatsapp = new URL("../assets/3d icon whatsapp.glb",import.meta.url)
      const theObjLoad_5 = new GLTFLoader()
      theObjLoad_5.load(thewhatsapp.href,(gltf) => {
        whatsapp = gltf.scene
        whatsapp.scale.set(0.54, 0.54, 0.54)
        whatsapp.position.set(30, -9.6, 2.8);
        whatsapp.rotation.y = 4.7
        scene.add(whatsapp);
})


let web
      const theWeb = new URL("../assets/logotipos_3d_-_aprenda_programar.glb",import.meta.url)
      const theWebLoad = new GLTFLoader()
      theWebLoad.load(theWeb.href,(gltf) => {
        web = gltf.scene
        web.scale.set(0.1, 0.1, 0.1)
        web.position.set(2,0,10);
        // web.rotation.y = 4.7
        scene.add(web);
})

      let background, planet_2,planet

    // loading 3D background object
    const house = new URL("../assets/Nebula HDRi 2.glb", import.meta.url)
    const houseLoader = new GLTFLoader()
    houseLoader.load(house.href, (gltf) => {
        background = gltf.scene
        background.scale.set(70,70,70)
        background.position.set(20, 0, 5);
        background.rotation.set(3,1,2)
        scene.add(background)

        planet = background.clone()
        planet.position.set(-3.1, 2, -5)
        planet.scale.set(2.5, 15.5, 10)
        planet.rotation.set(5,-2,6)
        scene.add(planet)

        planet_2 = background.clone()
        planet_2.position.set(20, 5, 25)
        planet_2.scale.set(1,1,1)
        planet_2.rotation.set(5,5,5)
        scene.add(planet_2)
})

      const raycaster = new THREE.Raycaster();
      const mouse = new THREE.Vector2();

      window.addEventListener('mousemove', (e) => {
          mouse.x = (e.clientX / window.innerWidth) * 2 - 1;
          mouse.y = -(e.clientY / window.innerHeight) * 2 + 1;
          raycaster.setFromCamera(mouse, camera);

      if (laptop) {
        const intersects = raycaster.intersectObject(laptop, true);

        if (intersects.length > 0) {
            gsap.to(laptop.rotation, {
                y: laptop.rotation.y + 1.8,
                duration : 0.7,
                ease : "power1.inOut"
            })
        }
    }
        const objects = [facebook, github, linkedin, whatsapp] 

        const intersects_2 = raycaster.intersectObjects(objects, true);
            if(intersects_2.length > 0){
                document.body.style.cursor = "pointer"
    
            //     window.open('https://www.facebook.com/omar.hamad.18294', '_blank');
            }else{
                document.body.style.cursor = "default"
            }
  })
      
      let angle = 0
      const animate = () => {
        requestAnimationFrame(animate);
        renderer.render(scene, camera);
        labelRender.render(scene, camera);

        if (facebook && github && linkedin && whatsapp) {
        angle += 0.008;
        const max = Math.PI / 45;
        const min = -Math.PI / 1.7;
    
        facebook.rotation.y = (max - min) / 12 * Math.sin(angle) + (max + min) / 1;
        github.rotation.y = (max - min) / 12 * Math.sin(angle) + (max + min) / 1;
        linkedin.rotation.y = (max - min) / 12 * Math.sin(angle) + (max + min) / 1;
        whatsapp.rotation.y = (max - min) / 12 * Math.sin(angle) + (max + min) / 1;
      }

        if(laptop){
            laptop.rotation.y += 0.001
        }

        if(background){
            background.rotation.z += 0.0005
        }
        if(planet_2){
            planet_2.rotation.x += 0.001
            planet_2.rotation.y += 0.001
        }
      }
      animate();

      // responsive
    window.addEventListener("resize", () => {
    camera.aspect = window.innerWidth / window.innerHeight
    camera.updateProjectionMatrix()
    renderer.setSize(window.innerWidth, window.innerHeight)
    labelRender.setSize(window.innerWidth, window.innerHeight)

})
    });

    
    return { theContainer, moveCamera, rotateCamera, goSkillsPage,
            goProjectsPage, goContactPage, goHomePage
     };
  
  }
}

</script>

<style lang="css">

  .homePage{
    width:100%;
    height: 100%;
    position: absolute;
    margin: 0%;
    padding: 0%;
    scroll-behavior: smooth;
    overflow: hidden;
  }
  .homeSection{
    padding-top: 33vh;
  }
  .one{
    display: flex;
    flex-direction: column;
  }
  .par{
    color: aliceblue;
    width: 55%;
  }
  .myLinks a{
    color: aliceblue;
    font-size: 20px;
    text-decoration: none;
    padding-left: 15px;
  }
  .myLinks{
    margin-left: 32px;
    transition: 0.3s ease;
  }
  .myLinks a:hover{
    color:aqua
  }
  .downloadButton{
    background-color: transparent;
    border: 1px solid aqua;
    border-radius: 20px;
    color:aqua;
    padding: 7px 30px ;
    font-weight: 600;
    text-align: center;
    border-left-width: 2px;
    border-right-width: 2px;
  }
  .backgroundImage{
    position: absolute;
    top: 0%;
    left: 5%;
  }

  @media (max-width:1200px){
    .homePage{
      overflow: hidden;
      overflow-x: hidden; 
      overflow-y: hidden;
    }
    
  .homeSection{
    padding-left: -15vh;
    margin-left: -10vh;
  }
  .one{
    display: flex;
    flex-direction: column;
    font-size: 16px;
  }
  .one h1{
    font-size: 24px;
  }
  .homePage .homeSection .one h2{
    font-size: 26px !important;
  }
  .homePage .homeSection .one h3{
    font-size: 25px !important;
  }
  .par{
    color: aliceblue;
    width: 53%;
    font-size: 18px;
  }
  .myLinks a{
    color: aliceblue;
    font-size: 20px;
    text-decoration: none;
    padding-left: 15px;
  }
  .myLinks{
    margin-left: 32px;
    transition: 0.3s ease;
    margin-top: -3vh;
  }
  .myLinks a:hover{
    color:aqua
  }
  .downloadButton{
    background-color: transparent;
    border: 1px solid aqua;
    border-radius: 20px;
    color:aqua;
    padding: 7px 30px ;
    font-weight: 900;
    font-size: 20px;
    text-align: center;
    border-left-width: 2px;
    border-right-width: 2px;
    margin-top: -3vh;
  }
  .backgroundImage{
    margin-left: -12vh;
    margin-top: -15vh;
  }
  }

  @media (max-width:1024px){
    .homePage{
      overflow: hidden;
      overflow-x: hidden; 
      overflow-y: hidden;
    }
  }

  @media (max-width:991px){
    .homeSection{
      display: flex;
      justify-content: center;
      flex-direction: column;
      margin-left: -12vh;
    }
    .homePage{
      display: flex;
      justify-content: center;
      flex-direction: column;
      overflow: hidden;
      overflow-x: hidden; 
      overflow-y: hidden;
    }
  .one h1{
    font-size: 23px;
  }
  .homePage .homeSection .one h2{
    font-size: 25px !important;
  }
  .homePage .homeSection .one h3{
    font-size: 23px !important;
  }
  .par{
    font-size: 17px;
  }
  }



  @media (max-width:768px){
    .homeSection{
      display: flex;
      justify-content: center;
      flex-direction: column;
      margin-left: -2vh;
    }
    .homePage{
      display: flex;
      justify-content: center;
      flex-direction: column;
      width:100%;
      height: 100%;
      margin: 0%;
      padding: 0%;
      overflow: hidden;
      overflow-x: hidden; 
      overflow-y: hidden;
    }
    .par{
      color: aliceblue;
      width: 86%;
      margin-top: 1.7vh;
      margin-left: -7.2vh;
      text-align: center;
      font-size: 15px;
    }
     .one h1{
      margin-left: 28vh;
    }
      
    .one h2{
      font-size: 30px;
      margin-left: 26vh;

    }
    .one h3{
      font-size: 18px;
      margin-left: 13vh;
      margin-top: 2vh;
    }
    .downloadButton{
      margin-left: 19vh;
      margin-bottom: 8vh;
  }
  .myLinks{
      margin-top: 7vh;
      margin-left: -35vh;
  }
  .backgroundImage{
    margin-bottom: 50vh;
  }

  }


  @media (max-width:617px){
    .homeSection{
      display: flex;
      justify-content: center;
      flex-direction: column;
    }
    .homePage{
      display: flex;
      justify-content: center;
      flex-direction: column;
      width:100%;
      height: 100%;
      margin: 0%;
      padding: 0%;
      overflow: hidden;
      overflow-x: hidden; 
      overflow-y: hidden;
    }
    .one h1{
      margin-left: 16vh;

    }
    .homePage .homeSection .one h2{
      margin-top: 1vh;
      margin-left: 15vh;
    }
    .one h3{
      font-size: 18px;
      margin-left: 2vh;
    }
    .par{
      color: aliceblue;
      width: 100%;
      margin-left: -12.2vh;
      margin-top: 2vh;
      text-align: center;
    }
    .downloadButton{
      margin-left: 9vh;
  }
  .backgroundImage{
    margin-top: -20vh;
  }
  }

  @media (max-width:450px){
    .homeSection{
      display: flex;
      justify-content: center;
      flex-direction: column;
    }
    .homePage{
      display: flex;
      justify-content: center;
      flex-direction: column;
      width:100%;
      height: 100%;
      margin: 0%;
      padding: 0%;
      overflow: hidden;
      overflow-x: hidden; 
      overflow-y: hidden;
    }
    .one h1{
      margin-left: 2vh;
    }
    .one h2{
      position: absolute;
      top: 41.2%;
      left: 18.7%;
      font-size: 30px;
      width: 100%;
    }
    .one h3{
      font-size: 18px;
      margin-left: -13vh;
      margin-top: 8vh;
    }
    .par{
      color: aliceblue;
      width: 125%;
      margin-left: -19.6vh;
      margin-top: 1vh;
    }
    .downloadButton{
      margin-left: -5vh;
      padding: 5px 17px;
      margin-top: -3vh;
  }
   .myLinks{
      padding-left: 2vh;
  } 
  .backgroundImage{
    margin-top: -42vh;
  }
  }

  @media (max-width:365px){
    .homeSection{
      display: flex;
      justify-content: center;
      flex-direction: column;
    }
    .homePage{
      display: flex;
      justify-content: center;
      flex-direction: column;
      width:100%;
      height: 100%;
      margin: 0%;
      padding: 0%;
      overflow: hidden;
      overflow-x: hidden; 
      overflow-y: hidden;
    }
    .one h1{
      position: relative;
      margin-left: -6vh;
    }
    .one h2{
      position: absolute;
      top: 42.2%;
      left: 12%;
      font-size: 30px;
      margin-top: 1vh;
    }
    .homePage .homeSection .one h3{
    font-size: 20px !important;
    margin-left: -16vh;
    margin-top: 9vh;
    width: 160%;
  }
  .par{
      width: 155%;
      margin-left: -22.3vh;
      font-size: 13px;
      margin-top: 1vh;
    }
    .downloadButton{
      margin-left: -12vh;
  }
  .backgroundImage{
    margin-top: -43vh;
  }
  
  }


  @media (max-width:320px){
    .homeSection{
      display: flex;
      justify-content: center;
      flex-direction: column;
    }
    .homePage{
      display: flex;
      justify-content: center;
      flex-direction: column;
      width:100%;
      height: 100%;
      margin: 0%;
      padding: 0%;
      overflow: hidden;
      overflow-x: hidden; 
      overflow-y: hidden;
    }
    .one h1{
      margin-left: -9vh;
    }
    .one h2{
      position: absolute;
      top: 41.8%;
      left: 7.3%;
    }
    .homePage .homeSection .one h3{
    margin-left: -20vh;
    margin-top: 8vh;
    width: 170%;
    font-style: 16px;
  }
  .par{
      width: 180%;
      margin-left: -24.3vh;
      font-size: 13px;
      margin-top: 2vh;
    }
    .downloadButton{
      padding: 5px 12px ;
      font-weight: 400;
      font-size: 17px;
      margin-right: 3vh;
  }
  .myLinks{
      padding-left: -3vh;
  }

  }


</style>