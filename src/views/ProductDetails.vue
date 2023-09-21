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
    <div>
    <img :src="product.image" alt="">
    <div>
        <span>{{ product.rating.rate }}</span>
        <span>{{ product.rating.count }}</span>
    </div>
    <h2>{{product.title}}</h2>
    <h3>${{product.price}}</h3>
    <h4>{{product.category}}</h4>
    <p>{{product.description}}</p>
    </div>  
        
</template>

<style scoped>

</style>