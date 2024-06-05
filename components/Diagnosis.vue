<template>
    <div class=" flex flex-col gap-1 h-[610px]">
        <h1 class="font-custom text-[#072635] font-extrabold text-[24px] mx-8 my-5">Diagnosis History</h1>

        <div class="bg-[#F4F0FE] rounded-xl w-[570px] h-[270px] mx-auto flex gap-6 px-1 pt-3">
           <div class="flex flex-col pl-1">
             <div class="flex justify-between px-4 mb-1">
                <span class="font-custom font-bold text-[11px] text-[#073625]">Blood pressure</span>
                <div class="flex gap-2 flex-row-reverse">
                    <img src="/public/Img/expand.svg" alt="" width="10" height="5" class="cursor-pointer">
                    <span class="font-custom font-medium text-[10px] text-[#073625]">last 6 months</span>
                </div>
             </div>
               <chart />
           </div>

           <div class="w-[200px] h-[170px] flex flex-col">
               <chartdetails />
           </div>
        </div>

        <div class="flex gap-2 mt-8 justify-evenly cursor-pointer">
            <div class="w-[180px] h-[200px] bg-[#E0F3FA] rounded-xl px-3 pt-3">
                <img src="/Img/diagnosis/respire.png" alt="" width="56" height="56">
                <div class="mt-5">
                    <span class="font-custom text-[#072635] text-[13px] font-medium">Respiratory rate</span>
                    <h2 class="font-custom text-[#072635] text-[25px] font-bold mb-2">{{ patient.respiratory_rate.value }}bpm</h2>
                    <span class="font-custom text-[#072635] text-[12px] font-medium">{{ patient.respiratory_rate.levels }}</span>
                </div>
            </div>
            <div class="w-[170px] h-[200px] bg-[#FFE6E9] rounded-xl px-3 pt-3">
                <img src="/Img/diagnosis/temp.png" alt="" width="56" height="56">
                <div class="mt-5">
                    <span class="font-custom text-[#072635] text-[13px] font-medium">Temperature</span>
                    <h2 class="font-custom text-[#072635] text-[25px] font-bold mb-2">{{ patient.temperature.value }}°F</h2>
                    <span class="font-custom text-[#072635] text-[12px] font-medium">{{ patient.temperature.levels }}</span>
                </div>
            </div>
            <div class="w-[170px] h-[200px] bg-[#FFE6E9] rounded-xl px-3 pt-3">
                <img src="/Img/diagnosis/heart.png" alt="" width="56" height="56">
                 <div class="mt-5">
                    <span class="font-custom text-[#072635] text-[13px] font-medium">Heart rate</span>
                    <h2 class="font-custom text-[#072635] text-[25px] font-bold mb-2">{{ patient.heart_rate.value }}bpm</h2>
                    <span class=" flex gap-2 items-center font-custom text-[#072635] text-[12px] font-medium"> 
                        <img src="/Img/diagnosis/downarrow.png" alt="" class="w-[10px] h-[5px]">
                        {{ patient.heart_rate.levels }}
                    </span>
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
const patient = ref([])



const { data, error } = await useFetch('https://fedskillstest.coalitiontechnologies.workers.dev', {
    headers: {
        'Authorization': 'Basic ' + btoa(`${username}:${password}`)
    }
})

if (error.value) {
    console.error('Error fetching data:', error.value)
} else if (data.value && data.value.length > 0) {
    patient.value = data.value[3].diagnosis_history[0]

}

</script>

<style scoped></style>