<template>
  <div class="home">
    <!-- landing markup -->
    <div class="landing shared">
      <img
        src="../assets/CatwikiLogo.svg"
        alt="landing image"
        class="landing-image"
      />
      <p class="landing-header">Get to know more about your cat breed</p>
      <Btn message="Get Started" styleing="success" class="get" />
    </div>
    <!-- most searched markup -->
    <div class="most-searched shared">
      <p class="searches"><span class="underline">Most S</span>earched Breed</p>
      <div class="discover--more">
        <h3 class="discover">66+ Breeds For you to discover</h3>
        <router-link class="more" to="/about">
          <p>SEE MORE</p>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M17 8l4 4m0 0l-4 4m4-4H3"
            />
          </svg>
        </router-link>
      </div>
      <div class="breed-grid">
        <div class="grid-item" v-for="breed in breeds" :key="breed.id">
          <img :src="breed.image.url" alt="Breed image" class="breed-image" />
          <h6 class="breed-name">{{ breed.name }}</h6>
        </div>
      </div>
    </div>
    <!-- why you should have a cat -->
  </div>
  <div class="why shared">
    <div class="why-content">
      <h3 class="why-content__header">Why should you have a cat?</h3>
      <p class="why--content__description">
        Having a cat around you can actually trigger the release of calming
        chemicals in your body which lower your stress and anxiety leves
      </p>
      <router-link class="see-why" to="/why">
        <p>READ MORE</p>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M17 8l4 4m0 0l-4 4m4-4H3"
          />
        </svg>
      </router-link>
    </div>
    <div class="why-image">
      <img src="../assets/wiki.png" alt="" />
    </div>
  </div>
</template>

<script setup>
// const { ref }=require("@vue/reactivity");
import { ref, onMounted } from "vue";
import Btn from "../components/Btn.vue";

const breeds = ref([]);

onMounted(() => {
  let API_KEY = "7c306308-15a5-45c8-9f7f-d215f10ddf53";
  fetch(`https://api.thecatapi.com/v1/breeds?api_key=${API_KEY}`)
    .then((res) => res.json())
    .then((result) => {
      let size = 4;
      let selected = result.slice(0, size);
      // console.log(selected)
      breeds.value = selected;
    });
});
</script>

<style scoped>
.home {
  border-radius: 10px;
  overflow: hidden;
  height: 150vh;
  display: grid;
  grid-template-rows: 1fr 1fr;
  /* align-items: center; */
}


.shared{
  padding-inline: 80px;
}


.landing {
  padding-inline: 80px;
  background: url("../assets/HeroImagelg.png");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  justify-content: center;
  color: white;
}

.landing-image {
  width: 250px;
  /* margin-top: 70px; */
  margin-bottom: 30px;
}

.landing-header {
  font-size: 24px;
  width: 360px;
  margin-bottom: 30px;
}

.get {
  width: 120px;
}

/* most searched styling */

.most-searched {
  color: #291507;
  padding: 20px;
  background: #e3e1dc;
  padding-inline: 80px;
}

.searches {
  color: #291507;
  margin-bottom: 50px;
}
.underline {
  border-bottom: 2px solid #4d270c;
}

.discover--more {
  display: flex;
}

.discover {
  font-size: 2.5rem;
  width: 450px;
}
.more {
  margin-left: auto;
  display: flex;
  text-decoration: none;
  color: #291507;
  align-self: center;
}

.more svg,
.see-why svg {
  width: 20px;
  margin-left: 10px;
}

.breed-grid {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  margin-top: 30px;
}

.breed-image {
  width: 200px;
  height: 200px;
  border-radius: 20px;
}

.grid-item{
  cursor: pointer;
}

.why {
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding-top: 50px;
  padding-bottom: 50px;
  justify-content: center;
  align-content: center;
  color: #291507;
}

.why-content {
  display: flex;
  flex-direction: column;
  /* align-items: center; */
  justify-content: center;
}

.why-content__header {
  font-size: 3rem;
}

.why--content__description{
  width: 400px;
  margin: 30px 0;
}

.see-why {
  display: flex;
  text-decoration: none;
  color: #291507;
}

.why-image img {
  width: 100%;
}

/* Responsive styling */
@media screen and (max-width: 1050px) {
  .home {
    height: 130vh;
  }

  .breed-image {
    width: 150px;
    height: 150px;
  }
}
@media screen and (max-width: 850px) {
  .home {
    height: 110vh;
    grid-template-rows: 1fr 1.8fr;
  }
  .landing {
    background: url("../assets/HeroImagesm.png");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
  }

  .shared{
    padding-inline: 50px;
  }

  .why{
    grid-template-columns: 1fr;
  }
}

@media screen and (max-width: 650px) {
  .home {
    height: 100vh;
    grid-template-rows: 1fr 2fr;
  }
  .landing {
    background: url("../assets/HeroImagesm.png");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
  }

  .shared{
    padding-inline: 30px;
  }

  .landing-image{
    width: 200px; 
    margin-bottom: 20px;
  }

  .landing-header{
    font-size: 20px;
  }
}

@media screen and (max-width: 450px){
  
  .landing-header{
    font-size: 15px;
    width: 200px;
  }
} 
</style>
