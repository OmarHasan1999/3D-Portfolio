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
import { onMounted, ref, nextTick } from 'vue';
import HeaderPage from '../components/HeaderPage.vue';
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

        // add home page to scene
          const home = document.querySelector(".homePage")
          const homeObject = new CSS2DObject(home);
          homeObject.position.set(38, 2.3, 8.7);
          scene.add(homeObject);

        // add skills to scene
          const skillsPage = document.querySelector(".skillsPage")
          const skillsObj = new CSS2DObject(skillsPage)
          skillsObj.position.set(0, -260, -300)
          scene.add(skillsObj)

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


      // adding 3D laptop model
      let laptop
      const theObj = new URL("../assets/3d_clipart_-_webdev.glb",import.meta.url)
      const theObjLoad = new GLTFLoader()
      theObjLoad.load(theObj.href,(gltf) => {
        laptop = gltf.scene
        adjustModelScale()
        scene.add(laptop);
        

})

      // adding 3D background objects
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

  // function to adjust the scale and position of the 3D models based on screen size
  function adjustModelScale() {
  if (!planet) return;
  if (!planet_2) return;

  else if (window.innerWidth <= 375) {
    laptop.scale.set(0.46, 0.5, 0.45); 
    laptop.position.set(10, -3.3, 8.9);

    planet.position.set(4.7, 2, -6.5)
    planet.scale.set(3.6, 16.6, 11.3)
    planet.rotation.set(5,-2,6)

    planet_2.position.set(20, 6, 14)
    planet_2.scale.set(0.8,0.8,0.8)

    earthPlanet.position.set(-7.5, -15, -5.4);
    earthPlanet.scale.set(2.2, 2.66, 2.6)

  }

  else if(window.innerWidth <= 450){
    planet_2.position.set(20, 6, 14)
    planet_2.scale.set(0.8,0.8,0.8)
    laptop.scale.set(0.5, 0.5, 0.5); 
    laptop.position.set(10, -3.3, 8.8);
    earthPlanet.position.set(-7, -15.5, -4.8);
    earthPlanet.scale.set(2.3, 2.8, 2.5)
  }

  else if(window.innerWidth <= 617){
    laptop.scale.set(0.58, 0.56, 0.5); 
    laptop.position.set(10, -3.3, 8.7);
    planet_2.position.set(20, 6, 17)
    earthPlanet.position.set(-7, -15.5, -4.8);
    earthPlanet.scale.set(3, 3, 3)
  }

  else if(window.innerWidth <= 768){
    laptop.scale.set(0.7, 0.6, 0.5); 
    laptop.position.set(10, -3.3, 9);
    planet_2.position.set(20, 6, 20)
    earthPlanet.position.set(-7, -15.4, -4.8);
    earthPlanet.scale.set(3, 3, 3)

  }

  else if(window.innerWidth <= 991){
    planet_2.position.set(20, 6, 20)
    laptop.position.set(22, -2, 16);
    laptop.scale.set(1.1, 1.4, 1.1); 
    earthPlanet.position.set(-7, -16, -4.8);
    earthPlanet.scale.set(3, 3, 3)
  }
  else if(window.innerWidth <= 1024){ 
    laptop.position.set(20, -2, 15);
    laptop.scale.set(1.1, 1.4, 1.1); 
    planet_2.position.set(22, 6, 22)
    earthPlanet.position.set(-7, -15, -4.8);
    earthPlanet.scale.set(3, 3, 3)

  }

  else if(window.innerWidth <= 1200){ 
  laptop.position.set(22, -1.4, 17);
  laptop.scale.set(1.1, 1.3, 1.1); 
  planet_2.position.set(22, 6, 25)
  earthPlanet.scale.set(3, 3, 3)

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


  }
}

      const animate = () => {
        requestAnimationFrame(animate);
        renderer.render(scene, camera);
        labelRender.render(scene, camera);


        if(laptop){
            laptop.rotation.y += 0.0014
        }

        if(earthPlanet){
            earthPlanet.rotation.y += 0.002
        }
        

        if(background){
            background.rotation.z += 0.0004
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
    if(laptop && planet && planet_2) adjustModelScale()
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

  @media (max-width:1200px){
    
    
  }

  @media (max-width:1024px){
    
    
  }

  @media (max-width:991px){
    
    
  }

</style>