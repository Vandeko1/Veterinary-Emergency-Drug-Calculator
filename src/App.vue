<script setup>
import Autocomplete from './components/Autocomplete.vue';
import drugs from './data/drugs.json'
import { ref } from 'vue';

const drug = ref('')
</script>
<template>
  <main>
    <div class="w-screen h-screen bg-gray-200 flex justify-start items-center flex-col">
      <div class="w-1/3 min-w-64 mt-8">
        <Autocomplete :source="drugs" v-model="drug" />
      </div>
      <div class="flex flex-col">
        <div class="overflow-x-auto sm:-mx-6 lg:-mx-8">
          <div class="inline-block min-w-full py-2 sm:px-6 lg:px-8">
            <div class="overflow-hidden">
              <table class="min-w-full text-left text-sm font-light text-surface dark:text-white">
                <thead class="border-b border-neutral-200 font-medium dark:border-white/10">
                  <tr>
                    <th scope="col" class="px-6 py-4">Тип</th>
                    <th scope="col" class="px-6 py-4">Підтип</th>
                    <th scope="col" class="px-6 py-4">Для собак</th>
                    <th scope="col" class="px-6 py-4">Для котів</th>
                  </tr>
                </thead>
                <tbody>
                  <tr class="border-b border-neutral-200 dark:border-white/10">
                    <td class="whitespace-nowrap px-6 py-4 font-medium">{{ drug.type }}</td>
                    <td class="whitespace-nowrap px-6 py-4">{{ drug.subtype }}</td>
                    <td class="whitespace-nowrap px-6 py-4">{{ drug.dogs }}</td>
                    <td class="whitespace-nowrap px-6 py-4">{{ drug.cats }}</td>
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
