<script setup>
// import { ref, } from 'vue';
import { ref, reactive } from 'vue';

const images = ref([  //REACTIVE IS NOT WORKING JUST CHECK REF AND CATCH SINGLE VALUE
  { id: 1, url: 'https://www.creativeitinstitute.com/images/course/course_1663052056.jpg' },
  { id: 2, url: 'https://www.creativeitinstitute.com/images/course/course_1673929467.jpg' },
  { id: 3, url: 'https://www.creativeitinstitute.com/images/course/course_1663052296.jpg' },
  { id: 4, url: 'https://www.creativeitinstitute.com/images/course/course_1663052131.jpg' },
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
          <img :src="image.url" alt="Carousel Image" class="w-full h-auto rounded-lg" />
        </div>
    </div>
    <div class="carousel-nav mt-5">
      <button @click="prevImage" class="carousel-nav-button  left bg-cyan-400 border-0">Previous</button>
      <button @click="nextImage" class="carousel-nav-button right btn bg-sky-400 ms-5 border-0">Next</button>
    </div>
  </div>
</template>

<style scoped></style>