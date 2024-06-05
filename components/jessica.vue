<template>
    <div>
        <div class="text-center mt-8 flex flex-col gap-4">
            <img :src="patient.profile_picture" alt="" class="mx-auto w-[150px] h-[150px]">
            <span class="font-custom font-bold text-[#072635] text-[24px]">{{ patient.name }}</span>
        </div>

        <section class="flex flex-col items-start gap-8 mt-8 px-6">
             <div class="flex justify-between items-center gap-2">
                <img src="/Img/jessica/birth.png" alt="" width="40" height="40">
                <div class="flex flex-col">
                  <span class="font-custom text-[#072635] font-normal text-[12px]">Date Of Birth</span>
                  <span class="font-custom text-[#072635] font-bold text-[14px]">{{ patient.date_of_birth }}</span>
                </div>
             </div>

             <div class="flex justify-between items-center gap-2">
                <img src="/Img/jessica/female.png" alt="" width="40" height="40">
                <div class="flex flex-col">
                  <span class="font-custom text-[#072635] font-normal text-[12px]">Gender</span>
                  <span class="font-custom text-[#072635] font-bold text-[14px]">{{ patient.gender }}</span>
                </div>
             </div>

             <div class="flex justify-between items-center gap-2">
                <img src="/Img/jessica/phone.png" alt="" width="40" height="40">
                <div class="flex flex-col">
                  <span class="font-custom text-[#072635] font-normal text-[12px]">Contact Info</span>
                  <span class="font-custom text-[#072635] font-bold text-[14px]">{{ patient.phone_number }}</span>
                </div>
             </div>

             <div class="flex justify-between items-center gap-2">
                <img src="/Img/jessica/phone.png" alt="" width="40" height="40">
                <div class="flex flex-col">
                  <span class="font-custom text-[#072635] font-normal text-[12px]">Emergency Contacts</span>
                  <span class="font-custom text-[#072635] font-bold text-[14px]">{{ patient.emergency_contact }}</span>
                </div>
             </div>

             <div class="flex justify-between items-center gap-2">
                <img src="/Img/jessica/insurance.png" alt="" width="40" height="40">
                <div class="flex flex-col">
                  <span class="font-custom text-[#072635] font-normal text-[12px]">Insurance Provider</span>
                  <span class="font-custom text-[#072635] font-bold text-[14px]">{{ patient.insurance_type}}</span>
                </div>
             </div>
        </section>

        <div class="text-center">
                <button class="rounded-[41px] px-6 py-3 mt-10 bg-[#01f0d0] font-custom font-bold text-[14px]">Show All Information</button>
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
    patient.value = data.value[3]
}
</script>

<style lang="scss" scoped>

</style>