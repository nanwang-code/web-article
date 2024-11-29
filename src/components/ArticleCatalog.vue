<script setup>
import ArticleCatalogItems from './ArticleCatalogItems.vue'
import { ref } from 'vue'
const art_items = ref({})
const loading = ref(true)

fetch("https://fakestoreapi.com/products").then((data) => data.json()).then((json) => { art_items.value = json; loading.value = false })

</script>

<template>

    <div class="Card" v-if="!loading">
        <ArticleCatalogItems v-for="article in art_items" :key="article.id" :articleitem="article"
            @sendDataToParent="showChildArtConsole" />
    </div>
    <div v-if="loading">
        <img class="loading" src="https://api.iconify.design/svg-spinners:tadpole.svg" alt="loading state" />
    </div>

</template>

<style>
.Card {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    /* flex-wrap: wrap;
    justify-content: space-between;
    align-items: center; */
}
</style>
