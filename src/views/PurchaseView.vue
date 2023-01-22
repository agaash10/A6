<script setup>
import { ref } from "vue";
import SiteModal from "../components/SiteModal.vue";
import { useStore } from "../store/index.js";

const store = useStore();
const genre = ref(28);
const showModal = ref(false);
const selectedId = ref(0);
const openModal = (id) => {
  showModal.value = true;
  selectedId.value = id;
};

const closeModal = () => {
  showModal.value = false;
};

const getGenres = async () => {
  await store.getMovies(genre.value);
};
</script>

<template>
  <div>
    <h1>
      Wondering what movie to watch next? <br />
      Here are several genres to choose from, click on the movie to get some cool info!
    </h1>
  </div>
  <RouterLink to="/cart" custom v-slot="{ navigate }">
    <button @click="navigate" role="link">Cart</button>
  </RouterLink>
  <select v-model="genre" class="dropdown" @change="getGenres()">
    <option value="28">Action</option>
    <option value="12">Adventure</option>
    <option value="878">Science Fiction</option>
    <option value="16">Animation</option>
    <option value="35">Comedy</option>
    <option value="18">Drama</option>
    <option value="10751">Family</option>

  </select>
  <div class="purchase-container">
    <img
      v-for="movie in store.movies"
      :id="movie.id"
      @click="openModal(movie.id)"
      :src="`https://image.tmdb.org/t/p/w500${movie.poster}`"
    />
    <SiteModal v-if="showModal" @toggleModal="closeModal()" :id="selectedId" />
  </div>
</template>

<style scoped>
h1 {
    color: rgb(255, 0, 0);
    border-color: rgb(0, 0, 0);
    border-width: 15px;
    border-style:dashed;
    font-family:'Times New Roman', Times, serif;
    padding: 20px;
    font-size: 25px;
   }

.purchase-container {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1rem;
}

img {
  width: 315px; 
  border-style:groove;
  border-color: rgb(0, 0, 0);
  border-width: 15px;
  margin-right: 10px;
  margin-top: 15px;
}


button {
  padding: 10px;
  width: 100px;
  font-size: 20px;
  font-family:'Times New Roman', Times, serif;
  border-color: rgb(255, 38, 0);
  border-width: 10px;
}
.dropdown {
  padding: 10px;
  width: 200px;
  font-size: 20px;
  font-family:'Times New Roman', Times, serif;
  border-color: rgb(255, 0, 0);
  border-width: 10px;
  margin-left: 10px;
}

</style>
