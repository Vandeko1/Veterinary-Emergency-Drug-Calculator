<script setup>
import { computed, ref, reactive } from 'vue';

const props = defineProps({
    source: {
        type: Array,
        required: true,
        default: () => []
    },

    modelValue: Object
})

const emit = defineEmits(['update:modelValue'])
const search = reactive({ 'name': '' })


const searchResults = computed(() => {
    if (search.name === '') {
        return []
    }

    return props.source.filter(item => {
        if (item.name.toLowerCase().includes(search.name.toLowerCase())) {
            return item
        }
    })

})

const isOpen = ref(false)
const setSelected = item => {
    isOpen.value = false
    search.name = 'item.name'
    emit('update:modelValue', item)
}

const handleInput = event => {
    isOpen.value = true
    search.name = event.target.value
    emit('update:modelValue', search)
}

const clearInput = () => {
    emit('update:modelValue', {})
}
</script>
<template>
    <div class="w-full relative input-wrapper">
        <input type="text" :value="modelValue.name" @input="handleInput"
            class="px-5 py-3 w-full border border-gray-300 rounded-md">
        <button v-show="search.name" @click="clearInput" class="w-9 h-9 mt-2 clear-btn">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
            </svg>
        </button>

        <ul v-show="searchResults.length && isOpen"
            class="mt-1 w-full max-h-60 border border-gray-300 rounded-md bg-white absolute overflow-y-auto">
            <li v-for="result in searchResults" :key="result.id" @click="setSelected(result)"
                class="px-4 py-3 border-b border-gray-200 text-stone-600 cursor-pointer hover:bg-gray-100 transition-colors">
                {{ result.name }}</li>
        </ul>
    </div>
</template>