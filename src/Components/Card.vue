<script setup lang="ts">

const props = defineProps({
  title: String,
  description: String,
  urlToImage: String,
  url: String,
  author: String,
  index: null,
})

const imgPlaceholder =
  'https://icon-library.com/images/no-image-available-icon/no-image-available-icon-6.jpg'
</script>

<template>

  <div
    class="bg-white rounded-xl overflow-hidden shadow-lg max-w-md mx-auto h-full md:max-w-2xl transform transition  active:scale-95 hover:scale-105"
    :class="index % 2 == 0 ? 'hover:-rotate-1' : 'hover:rotate-1'">
    <a class="h-full md:flex" :href="url">
      <div class="p-8">
        <div class="uppercase tracking-wide text-sm text-$color font-semibold">
          {{ author == null ? "" : author.length < 30 ?  author : ""  }}
        </div>
        <div class="block mt-1 leading-tight font-medium text-black hover:underline">
          <h2 class="font-semibold text-xl">{{ title }}</h2>
        </div>
        <p class="text-sm md:text-base mt-2 text-gray-500 line-clamp-3">
          {{ description == null ? '' : description }}
        </p>
      </div>
      <div class="flex md:flex-shrink-0 ">
        <img class="h-full w-full object-cover aspect md:w-48" :src="urlToImage == null ? imgPlaceholder : urlToImage"
          :alt="title" />
      </div>
    </a>
  </div>

</template>

<style>
.aspect {
  aspect-ratio: 16 / 9;
}
</style>
