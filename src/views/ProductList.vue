<script setup>
import { onBeforeMount, ref } from 'vue';
import axios from 'axios';

const products = ref([]);

console.log(products);


onBeforeMount(() => {
    fetch('https://fakestoreapi.com/products?limit=9')
        .then(res => res.json())
        .then(data => {products.value = data})
})

</script>

<template>
    <section class="my-20 mx-10">
    <h1 class="text-4xl text-center my-20 font-bold underline">Browse Products</h1>
    <div class="grid lg:grid-cols-3 md:grid-cols-2 sm:grid-cols-1 gap-10">
        <div v-for="product in products" :key="product.id" class="flex flex-col justify-center items-center px-10 py-5 space-y-5 rounded-lg shadow-md">
            <img class="w-[300px] h-[300px] " :src="product.image" alt="">
            <h2 class="text-2xl font-semibold">{{product.title}}</h2>
            <div class="flex items-center space-x-10">
                <h3 class="text-2xl font-semibold">${{product.price}}</h3>
            <router-link :to="`/product/${product.id}`"><button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">View Details</button></router-link>
            </div>
        </div>
    </div>
</section>
</template>

<style scoped>

</style>