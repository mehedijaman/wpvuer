<script setup>
import { inject } from 'vue';

const categories = inject('categories');
</script>
<template>
    <footer class="bg-white rounded-lg shadow m-4 dark:bg-gray-800">
        <div class="w-full mx-auto max-w-screen-xl p-4 md:flex md:items-center md:justify-between">
          <span class="text-sm text-gray-500 sm:text-center dark:text-gray-400">© 2023 <a href="/" class="hover:underline">WPVuer</a>. Licenced under MIT Licence.
        </span>
        <ul class="flex flex-wrap items-center mt-3 text-sm font-medium text-gray-500 dark:text-gray-400 sm:mt-0">

            <li v-for="(category,index) in categories" :key="index">
              <RouterLink class="mr-4 hover:underline md:mr-6" :to="`/posts?categories=${category.id}`" >{{ category.name }}</RouterLink>
            </li>
        </ul>
        </div>
    </footer>
</template>