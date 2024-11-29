<script setup>
defineProps(
   ["articleitem"]
)
</script>

<template>
   <div class="article">
      <div class="image">
         <img :src="articleitem.image">
         <div class="title"> {{ articleitem.title }} </div>
         <div class="star-icon">
            <img src="../assets/images/star-icon.png">
            <span class="rating">
               {{ articleitem.rating.rate }} ({{ articleitem.rating.count }}) votes </span>
         </div>
         <div class="sub"> {{ articleitem.description }} </div>

         <div class="price"> $ {{ articleitem.price }}</div>
         <button class="button" @click="$emit('sendDataToParent', articleitem.id)">В корзину</button>
      </div>
   </div>
</template>

<style>
.image {
   margin-bottom: 10px;
}

.image img {
   height: 300px;
   width: 300px;
}

.star-icon img {
   height: 20px;
   width: 20px;
}

.title {
   font-size: 20px;
}

.sub {
   font-size: 13px;
}
</style>