<template>
    <div class="px-4 py-4">
     <h1 class="font-custom font-bold text-[#073625] text-[20px] ml-4">Lab Results</h1>

     <div class="sidebar overflow-y-scroll h-[120px] w-[320px] mt-4 px-3">
       <div v-for="result in results" :key="result.name">
          <div  class="flex justify-between items-center px-3 py-3 hover:bg-[#F6F7F8]">
            <span class="font-custom text-[#072635] font-normal text-[14px]">{{ result }}</span>
            <img src="/Img/lab/download.png" alt="" width="20" height="20" class="cursor-pointer">
          </div>
          
       </div>
     </div>
    </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import { useFetch } from '#app'

const username = 'coalition'
const password = 'skills-test'
const results = ref([])



const { data, error } = await useFetch('https://fedskillstest.coalitiontechnologies.workers.dev', {
    headers: {
        'Authorization': 'Basic ' + btoa(`${username}:${password}`)
    }
})

if (error.value) {
    console.error('Error fetching data:', error.value)
} else if (data.value && data.value.length > 0) {
    results.value = data.value[3].lab_results
}
</script>

<style scoped>
.sidebar::-webkit-scrollbar {
  width: 6px;
  margin-left: 4px;
  /* Width of the scrollbar */
}

.sidebar::-webkit-scrollbar-track {
  background: #E3E4E6;
  /* Track color, Tailwind gray-800 */
  border-radius: 3px;
  /* Track border radius */
}

.sidebar::-webkit-scrollbar-thumb {
  background-color: #072635;
  border-radius: 6px;
  min-height: 3px;
}
</style>