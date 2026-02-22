<script setup>
import { RouterView } from 'vue-router'
import { ref, provide } from 'vue';

const showMenu = ref(false)
const scrollDown = ref(false)

const showLinks = () => {
  showMenu.value = !showMenu.value
}

provide("showMenu", showMenu)
provide("showLinks", showLinks)
provide("scrollDown", scrollDown)


</script>


<template>
    <RouterView />
</template>

<style lang="css">
*{
  margin: 0;
  padding: 0;
  scrollbar-width: none;
  scroll-behavior: smooth;
}

  body{
    overflow-x: hidden;
    overflow-y: auto;
    width: 100%;
    min-height: 100vh;
    margin: 0%;
    font-family: "Montserrat", sans-serif;

}
</style>
