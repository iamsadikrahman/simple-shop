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
    <section class="flex justify-center items-center h-screen space-x-36">
    <div>
    <img class="w-[300px]" :src="product.image" alt="">
    </div>
    <div class="flex flex-col space-y-5">
        <div class="flex items-center space-x-5 font-semibold ">
        <span>Rating: {{ product.rating.rate }}</span>
        <span>{{ product.rating.count }} Reviews</span>
    </div>
    <h2 class="text-3xl font-semibold">{{product.title}}</h2>
    <h3 class="text-2xl font-semibold">${{product.price}}</h3>
    <button class="w-2/12 bg-blue-500 hover:bg-blue-700 text-white font-bold py-4 px-4 rounded">Buy Now</button>
    <hr>
    <h4 class="text-xl font-semibold text-transform capitalize">{{product.category}}</h4>
    <hr>
    <p>{{product.description}}</p>
    </div>  
    </section>
        
</template>

<style scoped>

</style>