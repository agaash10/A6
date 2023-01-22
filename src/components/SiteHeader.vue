<script setup>
 
</script>

<template>
   <div>
      <h1> MOVIES WONDERLAND</h1>
      <RouterLink to="/login" custom v-slot="{ navigate }">
   <button @click="navigate" role="link">Login</button>
   </RouterLink>
   </div>
 
</template>

<style scoped>
 
h1 {
font-family: 'Times New Roman', Times, serif;
font-weight: bolder;
font-size: larger;
border-radius: 200%;
 }
 
button {
position: absolute;
padding: 30px;
}
 
</style>
 
 