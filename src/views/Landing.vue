<template>
  <div class="home">
    <div class="landing">
      <img
        src="../assets/CatwikiLogo.svg"
        alt="landing image"
        class="landing-image"
      />
      <p class="landing-header">Get to know more about your cat breed</p>
      <Btn message="Get Started" styleing="success" class="get"/>
      <!-- <form class="search" @submit.prevent="">
        <input type="text" placeholder="Enter your breed" />
        <button>🔍</button>
      </form> -->
      
    </div>
    <div class="most-searched">
      <h5>Most Searched Breed</h5>
      <div class="discover--more">
        <h3 class="discover">66+ Breeds For you to discover</h3>
        <p class="more">see more</p>
      </div>
      <div class="breed-grid">
        <div class="grid-item" v-for="breed in breeds" :key="breed.id">
          <img :src="breed.image.url" alt="Breed image" class="breed-image" />
          <h6 class="breed-name">{{ breed.name }}</h6>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// const { ref }=require("@vue/reactivity");
import { ref, onMounted } from "vue";
import Btn from "../components/Btn.vue"

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

.landing-header{
  font-size: 24px;
  width: 360px;
  margin-bottom: 30px;
}
/* .search {
  display: flex;
  padding: 10px;
  width: 300px;
  background: white;
  border-radius: 59px;
}

.search input {
  flex-grow: 2;
  border: none;
  outline: none;
}

.search button {
  border: none;
  background: none;
} */

.get{
  width: 120px;
}

.most-searched {
  color: #291507;
  padding: 20px;
  background: #e3e1dc;
}

.breed-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  align-items: center;
  justify-content: center;
}

.breed-image {
  width: 200px;
  height: 200px;
}
</style>
