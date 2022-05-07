<script setup lang="ts">
import Card from './Components/Card.vue'

let news = ref([])

onMounted(async () => {
  news.value = await fetch(
    'https://api.codetabs.com/v1/proxy?quest=https://newsapi.org/v2/top-headlines?country=eg&apiKey=f38f357a9e7d4b7dbcc3ece56bb5041d'
  )
    .then((response) => response.json())
    .then((data) => {
      console.log('done')
      return data.articles
    })
})
</script>

<template class="dark:bg-black">
  <h1 class="text-center text-5xl mb-10 font-bold text-red dark:text-white">اخبار مصر</h1>
  <div class="lg:grid lg:grid-cols-2 flex flex-col gap-10">
    <Card v-for="({ title, description, urlToImage, url, author }, index) in news" :title="title"
      :description="description" :urlToImage="urlToImage" :url="url" :author="author" :index="index" />
  </div>
</template>

<style>
:root {
  --color: #ff5a5a;
}

a {
  text-decoration: none;
}

@media (prefer-color-scheme : dark) {
  body {
    background-color: #5a5a5a;
  }
}


body {
  padding: 0 2rem;
  padding-bottom: 1.5rem;
  background-color: #f3f3f3;
}

* {
  font-family: 'Cairo', sans-serif;
}
</style>
