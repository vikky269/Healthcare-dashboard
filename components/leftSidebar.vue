<template>
  <aside class="bg-white w-[300px] h-[930px] rounded-[16px] mt-12 pt-5">
    <div class="flex justify-between items-center mb-5 px-4">
      <h1 class="text-[20px] text-[#072635] font-bold font-custom ml-2">Patients</h1>
      <img src="/Img/leftsidebar/search.png" alt="" class="w-[20px] h-[20px]">
    </div>


    <div class="sidebar overflow-y-scroll w-[290px] h-[850px]">
      <div v-for="patient in patients" :key="patient.name" class="px-4 pt-2 pb-1 hover:bg-[#D8FCf7] cursor-pointer">
        <div class="flex justify-between items-center mb-4">
          <div class="flex justify-between items-center gap-3">
            <img :src="patient.profile_picture" alt="" width="48" height="48">
            <div class="flex flex-col justify-center">
              <h1 class="font-custom font-bold text-[12px] text-[#072635]">{{ patient.name }}</h1>
              <span class="font-normal text-[#707070] text-left font-custom text-[10px]">{{ patient.gender }}, {{patient.age }}</span>
            </div>
          </div>

          <div class="z-[50]">
            <img src="/Img/leftsidebar/more.png" alt="">
          </div>
        </div>
      </div>
    </div>
  </aside>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import { useFetch } from '#app'

const username = 'coalition'
const password = 'skills-test'
const patients = ref([])
 
const { data, error } = await useFetch('https://fedskillstest.coalitiontechnologies.workers.dev', {
    headers: {
      'Authorization': 'Basic ' + btoa(`${username}:${password}`)
    }
  })
  
  if (error.value) {
    console.error('Error fetching data:', error.value)
  } else if (data.value && data.value.length > 0) {
    patients.value = data.value
  }

</script>

<style scoped>
.sidebar::-webkit-scrollbar {
  width: 6px;
}

.sidebar::-webkit-scrollbar-track {
  background: #E3E4E6;
  border-radius: 3px;
}

.sidebar::-webkit-scrollbar-thumb {
  background-color: #072635;
  border-radius: 6px;
  height: -10px;
}
</style>