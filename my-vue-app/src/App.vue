<script setup lang="ts">
import axios from 'axios';
import { onMounted, ref } from 'vue';
import Navbar from './layout/navbar.vue';
import Users from './components/users/users.vue';
import Search from './components/users/search.vue';
const users = ref([]);
onMounted (() => {
  const fetchData = async() =>{
    try{
      const response = await axios.get("https://api.github.com/users");
      console.log("Github Users:", response.data);
      users.value = response.data;
    }
    catch (error){
      console.error("Error fetching data", error);
    }
  };
  fetchData();
});
</script>

<template>
  <Navbar />
  <div class="container">
    <h1>Hello World</h1>
    <Search />
    <Users :users="users"/>
  </div>
</template>