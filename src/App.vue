<template>
<div class="container">
  <NavBar />
  <router-view />
</div>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav> -->
</template>

<script setup>
import NavBar from "./components/NavBar.vue";
</script> 

<style>

@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&display=swap');

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  min-height: 100vh;
  font-family: "Montserrat", sans-serif;
}


.container{
  padding-inline: 80px;
}
</style>
