<script setup>
import Autocomplete from './components/Autocomplete.vue';
import drugs from './data/drugs'
import { ref } from 'vue';

const drug = ref('')
</script>
<template>
  <header class="sticky top-0 z-20 flex items-center justify-between border-b bg-yellow">
    <a href="#">
      <img src="./assets/logo.png" alt="Logo" class="h-9">
    </a>
    <a href="#">На вебсайт</a>
  </header>
  <main>
    <div class="w-screen h-screen bg-gray-200 flex justify-center items-center flex-col">
      <div class="w-1/3">
        <h1 class="text-center mb-3 font-bold">{{ drug }}</h1>
        <Autocomplete :source="drugs" v-model="drug" />
      </div>
      <div class="flex flex-col">
        <div class="overflow-x-auto sm:-mx-6 lg:-mx-8">
          <div class="inline-block min-w-full py-2 sm:px-6 lg:px-8">
            <div class="overflow-hidden">
              <table
                class="min-w-full text-left text-sm font-light text-surface dark:text-white">
                <thead
                  class="border-b border-neutral-200 font-medium dark:border-white/10">
                  <tr>
                    <th scope="col" class="px-6 py-4">Тип</th>
                    <th scope="col" class="px-6 py-4">Підтип</th>
                    <th scope="col" class="px-6 py-4">Для собак</th>
                    <th scope="col" class="px-6 py-4">Для котів</th>
                  </tr>
                </thead>
                <tbody>
                  <tr class="border-b border-neutral-200 dark:border-white/10">
                    <td class="whitespace-nowrap px-6 py-4 font-medium">Обезболюючий</td>
                    <td class="whitespace-nowrap px-6 py-4">Передопераційний</td>
                    <td class="whitespace-nowrap px-6 py-4">1.5</td>
                    <td class="whitespace-nowrap px-6 py-4">1.5</td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
