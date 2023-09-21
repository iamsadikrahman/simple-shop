<script setup>
import { onBeforeMount, ref } from 'vue';
import axios from 'axios';

const products = ref([]);

console.log(products);


onBeforeMount(() => {
    fetch('https://fakestoreapi.com/products')
        .then(res => res.json())
        .then(data => {products.value = data})
})





</script>

<template>
    <div>
        <div v-for="product in products" :key="product.id">
            <img :src="product.image" alt="">
            <h2>{{product.title}}</h2>
            <h3>${{product.price}}</h3>
            <router-link :to="`/product/${product.id}`"><button>View Details</button></router-link>

        </div>
    </div>
</template>

<style scoped>

</style>