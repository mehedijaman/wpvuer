<script setup>
import { ref, inject } from 'vue';

const baseUrl = inject('baseUrl')
let showModal = ref(false)

</script>
<template>
  <nav class="bg-white dark:bg-gray-900 fixed w-full z-20 top-0 left-0 border-b border-gray-200 dark:border-gray-600">
    <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
    <RouterLink to="/" class="flex items-center">
        <img src="https://mehedipata.com/wp-content/uploads/2022/06/cropped-Profile-32x32.jpg" class="h-8 mr-3 rounded-full" alt="MehediPata Logo">
        <span class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white">WPVuer</span>
    </RouterLink>
    <div class="flex md:order-2">
        <button @click.prevent="showModal = true" type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-4 py-2 text-center mr-3 md:mr-0 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Change API Endpoint</button>
        <button data-collapse-toggle="navbar-sticky" type="button" class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600" aria-controls="navbar-sticky" aria-expanded="false">
          <span class="sr-only">Open main menu</span>
          <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 14">
              <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 1h15M1 7h15M1 13h15"/>
          </svg>
      </button>
    </div>
    <div class="items-center justify-between hidden w-full md:flex md:w-auto md:order-1" id="navbar-sticky">
      <ul class="flex items-center p-4 md:p-0 mt-4 font-medium border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 md:mt-0 md:border-0 md:bg-white dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700">
        <li>
            <RouterLink to="/" class="block py-2 pl-3 pr-4 text-white bg-blue-700 rounded md:bg-transparent md:text-blue-700 md:p-0 md:dark:text-blue-500" aria-current="page">Home</RouterLink>
        </li>
        <li>
          <RouterLink to="/contact" class="block py-2 pl-3 pr-4 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:hover:text-blue-700 md:p-0 md:dark:hover:text-blue-500 dark:text-white dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent dark:border-gray-700">Contact</RouterLink>
        </li>
        <li>
          <p class="p-2 items-center flex rounded-md bg-gray-200">Showing Content From : <span class="text-red-500 pl-2">{{ baseUrl }}</span></p>
        </li>
      </ul>
    </div>
    </div>
  </nav>

  <!-- component -->
  <div v-show="showModal" class="fixed left-0 top-0 flex h-full w-full items-center justify-center bg-black bg-opacity-50 py-10">
    <div class="max-h-full w-full max-w-xl overflow-y-auto sm:rounded-2xl bg-white">
      <div class="w-full">
        <div class="m-8 my-20 max-w-[400px] mx-auto">
          <div class="mb-8">
            <h1 class="mb-4 text-3xl font-extrabold">Change Wordpress API</h1>
            <input v-model="baseUrl" type="text" class="w-full py-2 px-5 focus:outline-none border border-black rounded-2xl" placeholder="e.g. https://mehedipata.com/wp-json/wp/v2">
          </div>
          <div class="space-y-4">
            <button @click.prevent="$emit('changeAPI')" class="p-3 bg-black rounded-full text-white w-full font-semibold">Change API</button>
            <button @click="showModal=false" class="p-3 bg-white border rounded-full w-full font-semibold">Cancel</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>