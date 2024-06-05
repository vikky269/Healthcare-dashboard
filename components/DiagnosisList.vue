<template>
    <div>
        <h1 class="text-[16px] text-[#072635] font-custom font-bold ml-4">Diagnostic List</h1>

        <div class="mt-4">

            <table class="border-collapse">
                <tr
                    class="table-header mx-auto w-[550px] bg-[#F6F7F8] rounded-3xl flex gap-24 mt-4 px-3 mb-3 py-3">
                    <td class="text-[12px] text-[#072635] font-custom font-bold">Problem/Diagnosis</td>
                    <td class="text-[12px] text-[#072635] font-custom font-bold ml-[5px]">Description</td>
                    <td class="text-[12px] text-[#072635] font-custom font-bold ml-16">Status</td>
                </tr>
                <div class="sidebar overflow-y-scroll h-[120px] w-[570px]">
                    <tr v-for="disease in patient" :key="disease.name" >

                        <div class="w-[550px] mx-auto my-2 flex justify-between">
                            <td class="text-[13px] text-[#072635] font-normal ml-[20px] font-custom ">{{ disease.name }}</td>
                            <td class="text-[13px] text-[#072635] font-normal font-custom">{{ disease.description }}</td>
                            <td class="text-[13px] text-[#072635] font-normal font-custom">{{ disease.status }}</td>
                        </div>
                        <hr>

                    </tr>
                </div>
            </table>
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
    patient.value = data.value[3].diagnostic_list
    console.log(patient.value)
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