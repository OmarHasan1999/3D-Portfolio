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

    <div class="loadingPage">
        <h1 class="heading">Welcome To My Website!</h1>
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
    const homeObjectRef = ref(null);
    const skillsObjectRef = ref(null);
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
            moveCamera(-38, 31, -8)
            rotateCamera(-0.6, 0, 0)
            if (headerObjectRef.value) {
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
            rotateCamera(0, 0.5 , 0)
            if (headerObjectRef.value) {
                headerObjectRef.value.position.set(-6.8, -7, -4);
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
      setTimeout(() => {
        const mainContainer = document.querySelector(".theContainer")
        const loading = document.querySelector(".loadingPage")
        mainContainer.style.display = "block"
        loading.style.display = "none"
      }, 3000);

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
          scene.add(headerObject);
          headerObject.position.set(38, 17.2, 8.7);
          headerObjectRef.value = headerObject;
          //adjustModelScale()

        // add home page to scene
          const home = document.querySelector(".homePage")
          const homeObject = new CSS2DObject(home);
          scene.add(homeObject);
          homeObjectRef.value = homeObject
          adjustModelScale()

        // add skills to scene
          const skillsPage = document.querySelector(".skillsPage")
          const skillsObj = new CSS2DObject(skillsPage)
          scene.add(skillsObj)
          skillsObjectRef.value = skillsObj
          adjustModelScale()

          // add projects page to scene
          const projectsPage = document.querySelector(".projectsPage")
          const projectsObject = new CSS2DObject(projectsPage);
          projectsObject.position.set(-6.7, 1.6, -4);
          scene.add(projectsObject);

          // add contact to scene
          const contact = document.querySelector(".contactPage")
          const contactObj = new CSS2DObject(contact)
          contactObj.position.set(-6.4,-11.4,-4)
          scene.add(contactObj)
      })


      let laptop
      const theObj = new URL("../assets/3d_clipart_-_webdev.glb",import.meta.url)
      const theObjLoad = new GLTFLoader()
      theObjLoad.load(theObj.href,(gltf) => {
        laptop = gltf.scene
        adjustModelScale()
        scene.add(laptop);

})


      let background, planet_2,planet, earthPlanet

    // loading 3D background object
    const house = new URL("../assets/stars.glb", import.meta.url)
    const houseLoader = new GLTFLoader()
    houseLoader.load(house.href, (gltf) => {
        background = gltf.scene
        background.scale.set(70,70,70)
        background.position.set(20, 0, 5);
        background.rotation.set(3,1,2)
        adjustModelScale()
        scene.add(background)

        planet = background.clone()
        adjustModelScale()
        scene.add(planet)

        planet_2 = background.clone()
        adjustModelScale()
        scene.add(planet_2)

})

    const earth = new URL("../assets/planet_earth.glb", import.meta.url)
    const earthLoader = new GLTFLoader()
    earthLoader.load(earth.href, (gltf) => {
        earthPlanet = gltf.scene
        scene.add(earthPlanet)
        adjustModelScale()

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

  })


  function adjustModelScale() {
  if (!planet) return;
  if (!planet_2) return;
  if(!homeObjectRef.value) return
  if(!skillsObjectRef.value) return

  if (window.innerWidth <= 320) {
    laptop.position.set(8, -3.4, 9.3);
    laptop.rotation.y = 4.3
    laptop.scale.set(0.2, 0.3, 0.2);

    planet.position.set(4.7, 2, -5)
    planet.scale.set(2.5, 15.5, 10)
    planet.rotation.set(5,-2,6)

    planet_2.position.set(20, 6, 13)
    planet_2.scale.set(1,1,1)
    planet_2.rotation.set(5,5,5)

    earthPlanet.position.set(-7, -15, -4.8);
    earthPlanet.scale.set(2.4, 2.5, 2.4)
  } 

  else if (window.innerWidth <= 375) {
    laptop.scale.set(0.6, 0.7, 0.6); 
    laptop.position.set(22, -8.2, 10.5);

    planet.position.set(4.7, 2, -6.5)
    planet.scale.set(3.6, 16.6, 11.3)
    planet.rotation.set(5,-2,6)

    planet_2.position.set(20, 6, 14)
    planet_2.scale.set(0.8,0.8,0.8)

    earthPlanet.position.set(-7, -15.5, -5.4);
    earthPlanet.scale.set(2.6, 2.6, 2.6)

  }

  else if(window.innerWidth <= 450){
    planet_2.position.set(20, 6, 14)
    planet_2.scale.set(0.8,0.8,0.8)
    laptop.scale.set(0.6, 0.7, 0.6); 
    laptop.position.set(22, -5, 14);
    earthPlanet.position.set(-7, -15.9, -5);

  }

  else if(window.innerWidth <= 617){
    laptop.scale.set(0.7, 0.9, 0.7); 
    laptop.position.set(22, -3, 16);
    planet_2.position.set(20, 6, 17)
  }

  else if(window.innerWidth <= 768){
    laptop.scale.set(0.9, 1, 0.9); 
    laptop.position.set(10, 3, 8);
    planet_2.position.set(20, 6, 20)
  }

  else if(window.innerWidth <= 991){
    skillsObjectRef.value.position.set(40, -230, -300)
    planet_2.position.set(20, 6, 20)
    laptop.position.set(22, -2.6, 16);
    laptop.scale.set(0.9, 1.1, 1.1); 
  }
  else if(window.innerWidth <= 1024){ 
    laptop.position.set(22, -3.4, 16);
    laptop.scale.set(1, 1.1, 1); 
    planet_2.position.set(22, 6, 22)
    skillsObjectRef.value.position.set(30, -223, -300)

  }

  else if(window.innerWidth <= 1200){ 
  homeObjectRef.value.position.set(38, 2.3, 11);
  skillsObjectRef.value.position.set(0, -230, -300)
  laptop.position.set(22, -2.7, 17);
  laptop.scale.set(1.1, 1.2, 1.1); 
  planet_2.position.set(22, 6, 25)

  }
  
  else {
    laptop.position.set(20, -3, 17);
    laptop.scale.set(1.2, 1.3, 1.2); 
    laptop.rotation.y = 4.3

    planet.position.set(-3.1, 2, -5)
    planet.scale.set(2.5, 15.5, 10)
    planet.rotation.set(5,-2,6)

    planet_2.position.set(20, 5, 25)
    planet_2.scale.set(1,1,1)
    planet_2.rotation.set(5,5,5)

    earthPlanet.scale.set(3, 3, 3)
    earthPlanet.position.set(-7, -15.9, -6);

    homeObjectRef.value.position.set(38, 2.3, 8.7);
    skillsObjectRef.value.position.set(0, -260, -300)

  }
}

      const animate = () => {
        requestAnimationFrame(animate);
        renderer.render(scene, camera);
        labelRender.render(scene, camera);


        if(laptop){
            laptop.rotation.y += 0.001
        }

        if(earthPlanet){
            earthPlanet.rotation.y += 0.001
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
    renderer.setPixelRatio(window.devicePixelRatio);
    if(laptop && planet && planet_2 && homeObjectRef &&
      skillsObjectRef
    ) adjustModelScale()
})
})

    return { theContainer, moveCamera, rotateCamera, goSkillsPage,
            goProjectsPage, goContactPage, goHomePage
     };

  }
  }

</script>

<style lang="css">

.theContainer {
  display:none;
}

.loadingPage{
    position: fixed;
    top: 0%;
    left: 0%;
    color: white;
    background-color: black;
    width: 100%;
    height: 100vh;
    text-align: center;
    line-height: 90vh;
    z-index: 999;
}

@keyframes heading{
    from{
        opacity: 0;
    }
    to{
        opacity: 1;
    }
}

.heading{
    /* opacity: 0; */
    animation: heading 1.3s ease-in forwards;
}

/* Responsive section */
@media (max-width:320px){
  .heading{
    font-size: 20px;
}
}

@media (max-width:375px){
  .heading{
    font-size: 20px;
}
}

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