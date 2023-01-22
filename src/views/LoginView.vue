<script setup>
import SiteFooter from "../components/SiteFooter.vue";
import { ref } from "vue";
import { useRouter } from "vue-router";
const router = useRouter();
const username = ref("");
const password = ref("");
const error = ref(false);
const login = () => {
  
 if (username.value === "tmdb" && password.value === "movies") {
   router.push("/purchase");
 } else {
   error.value = true;
 }
};
</script>

<template>
 <div class="login-container">
   <h1> Please login with username and password to browse movies.</h1>
   <form @submit.prevent="login()">
     <input type="text" v-model="username" placeholder="Username" />
     <input type="password" v-model="password" placeholder="Password" />
     <input type="submit" value="Login" />
   </form>
   <div v-if="error" class="error">
     <p>Incorrect! Hint: use tmdb for username and movies for password</p>
   </div>
 </div>
 <div>
        <SiteFooter />
    </div>
</template>

<style scoped>

form {
 display: flex;
 flex-direction: column;
 
}
 
form input {
 color: rgb(253, 7, 7);
 font-size: 20px;
 height: 65px;
 border-color: rgb(0, 0, 0);
 border-width: 5px;
 font-family: 'Times New Roman', Times, serif;
 
}
 
h1 {
  font-size: 30px;
  font-weight: bolder;
  font-family: 'Times New Roman', Times, serif;
}
 
 
footer {
  font-size: 20px;
  font-family:'Times New Roman', Times, serif;
  padding: 5px;
  background-color: rgb(255, 0, 0);
  color: rgb(0, 0, 0);
  top: 20px
}
</style>
