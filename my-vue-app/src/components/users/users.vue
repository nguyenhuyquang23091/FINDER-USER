<script setup>
import useritem from './useritem.vue';
const props = defineProps({
    users: {
        type: Array,
        required: true,
    }
})
const userStyle ={
    display: "grid",
    gridTemplateColumns: "repeat(3, 1fr)",
    gridGap: "1rem",
}
</script>
<template>
    <div :style="userStyle">
        <useritem v-for ="user in users" :key="user.id" :user="user"/>
    </div>
</template>
<style scoped></style>