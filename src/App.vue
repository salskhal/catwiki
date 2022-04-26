<template>
<div class="container">
  <NavBar />
  <router-view />
  <Footer class="footer"/>
</div>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav> -->
</template>

<script setup>
import NavBar from "./components/NavBar.vue";
import Footer from "./components/Footer.vue";
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
  display: flex;
  flex-direction: column;
}

.footer{
  margin-top: auto;
}


/* responsive design */
@media screen and (max-width: 800px){
  .container{
    padding-inline: 60px;
  }
}

@media screen and (max-width: 650px){
  .container{
    padding-inline: 20px;
  }
}

</style>
