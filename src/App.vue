<script setup>
// import { ref, } from 'vue';
import { ref, reactive } from 'vue';

const images = ref([  //catch single card value
  { id: 1, url: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60" },
  { id: 2, url: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60" },
  { id: 3, url: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60" }
]);

const currentImage = ref(1);

const nextImage = () => {
  currentImage.value = currentImage.value == images.value.length ? 1 : currentImage.value + 1;
};

const prevImage = () => {
  currentImage.value = currentImage.value == 1 ? images.value.length : currentImage.value - 1;
};
</script>

<template>
  <div class="carousel-container border p-5 bg-sky-200">
    <h1 class="mb-10">This is my Carousel </h1>
    <div class="carousel">
        <div v-for="image in images" :key="image.id" v-show="image.id == currentImage ">
          <img :src="image.url" alt="Carousel Image" class="w-50% h-auto rounded-lg" />
        </div>
    </div>
    <div class="carousel-nav mt-5">
      <button @click="prevImage" class="carousel-nav-button  left bg-cyan-400 border-0">Previous</button>
      <button @click="nextImage" class="carousel-nav-button right btn bg-sky-400 ms-5 border-0">Next</button>
    </div>
  </div>
</template>

<style scoped></style>