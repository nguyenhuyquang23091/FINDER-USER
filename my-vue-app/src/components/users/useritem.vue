<script setup>
const props = defineProps({
    user :{
        type: Object,
        required: true,
    }
});
</script>

<template>
    <div class = "card text-center">
        <img :src="user.avatar_url" alt="" class="round-img" style="width:60px">
        <h3>{{user.login}}</h3>
        <div>
            <a href="#" class ="btn btn-dark btn-sm my-1">More</a>
        </div>
    </div>
</template>
<style scoped>
.round-img{
    border-radius: 50%;
}
</style>