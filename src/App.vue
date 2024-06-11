<script setup>
import Autocomplete from './components/Autocomplete.vue';
import drugs from './data/drugs.json'
import { ref } from 'vue';

const drug = ref('')
</script>
<template>
  <main>
    <div class="wrapper p-2.5">
      <Autocomplete :source="drugs" v-model="drug" />
      <table v-for="item in drug.data" :key=item.id
        class="mt-2.5 border-collapse w-full border border-slate-400 dark:border-slate-500 bg-white dark:bg-slate-800 text-sm shadow-sm">
        <thead class="bg-slate-50 dark:bg-slate-700">
          <tr>
            <th class="border border-slate-300 dark:border-slate-700 p-4 text-slate-500 dark:text-slate-400">Властивість
            </th>
            <th class="border border-slate-300 dark:border-slate-700 p-4 text-slate-500 dark:text-slate-400">Значення
            </th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td class="border border-slate-300 dark:border-slate-700 p-4 text-slate-500 dark:text-slate-400">Група</td>
            <td class="border border-slate-300 dark:border-slate-700 p-4 text-slate-500 dark:text-slate-400">{{
              item.type }}</td>
          </tr>
          <tr>
            <td class="border border-slate-300 dark:border-slate-700 p-4 text-slate-500 dark:text-slate-400">Місце
              введення</td>
            <td class="border border-slate-300 dark:border-slate-700 p-4 text-slate-500 dark:text-slate-400">{{
              item.place }}</td>
          </tr>
          <tr>
            <td class="border border-slate-300 dark:border-slate-700 p-4 text-slate-500 dark:text-slate-400">Для собак
            </td>
            <td class="border border-slate-300 dark:border-slate-700 p-4 text-slate-500 dark:text-slate-400">{{
              item.dogs }}</td>
          </tr>
          <tr>
            <td class="border border-slate-300 dark:border-slate-700 p-4 text-slate-500 dark:text-slate-400">Для котів
            </td>
            <td class="border border-slate-300 dark:border-slate-700 p-4 text-slate-500 dark:text-slate-400">{{
              item.cats }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </main>
</template>
<style>
.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
