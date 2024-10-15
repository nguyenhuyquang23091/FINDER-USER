<script setup>
import { ref } from 'vue';
import axios from 'axios';
import Users from './users.vue';
const text = ref('');
const users = ref([]);
const searchusers = async (searchText) =>{
    try{
        const response = await axios.get(`https://api.github.com/search/users?q=${searchText}`);
        users.value = response.data.items;
    } catch(error){
        console.error("Error fetching data", error);
    }
}
const onSubmit = () =>{
    if (text.value === ""){
        alert("Please enter something");
    } else{
        searchusers(text.value);
        text.value = "";
    }
};
const clearUsers = () =>{
    users.value = [];
};
</script>
<template>
    <div>
        <form @submit.prevent="onSubmit" class="form">
            <input type="text" name="text" placeholder="Search Users..." v-model="text"/>
            <input type="submit" value="Search" class="btn btn-dark btn-block"/>
        </form>
        
        <button
            @click="clearUsers"
            v-if="users.length > 0"
            class="btn btn-block btn-danger"
            >
            Clear
            </button>

            <Users :users="users" />
    </div>
</template>
<style scoped>
/* Add any specific styles if needed */
</style>