<script setup>

import { onBeforeMount, ref } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute()

const product = ref({})



onBeforeMount(() => {
    fetch(`https://fakestoreapi.com/products/${route.params.id}`)
        .then(res => res.json())
        .then(data => {
            product.value = data
        })
})
</script>

<template>
    <section class="flex sm:flex-row flex-col justify-center items-center md:h-screen my-10 mx-5">
    <div class="w-6/12 ">
    <img class="w-[300px] mx-auto" :src="product.image" alt="">
    </div>
    <div class="flex flex-col space-y-5 md:w-6/12 justify-center items-center ">
        <div class="flex items-center space-x-5 font-semibold ">
        <span>Rating: {{ product.rating.rate }}</span>
        <span>{{ product.rating.count }} Reviews</span>
    </div>
    <h2 class="md:text-3xl text-2xl font-semibold">{{product.title}}</h2>
    <h3 class="text-2xl font-semibold">${{product.price}}</h3>
    <button class="w-[100px] bg-blue-500 hover:bg-blue-700 text-white font-bold py-4 px-4 rounded">Buy Now</button>
    <hr>
    <h4 class="text-xl font-semibold text-transform capitalize">{{product.category}}</h4>
    <hr>
    <p>{{product.description}}</p>
    </div>  
    </section>
        
</template>

<style scoped>

</style>