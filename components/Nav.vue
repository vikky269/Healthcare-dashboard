<template>
    <nav class="bg-white rounded-[70px] h-[72px] flex justify-evenly items-center sticky top-0 z-20">
<!--nav logo-->
        <div class="ml-10 cursor-pointer">
            <img src="/Img/nav/TestLogo.png" alt="logo" class="w-[180px] h-[40px]">

        </div>

<!--nav link items-->
        <div class="flex justify-center ml-[7rem]">
            <div v-for="item in navItem" :key="item.content" class="cursor-pointer flex items-center justify-center gap-3 hover:bg-[#01F0D0] hover:rounded-[41px] w-[140px] h-[41px]">
                <img :src="item.img" alt="" class="w-[18.5px]">
                <NuxtLink  to="/" class="text-[#072635] font-bold text-[15px]">{{ item.content }}</NuxtLink>
            </div>
        </div>

       <!--woman logo-->
        <div class="flex justify-between items-center gap-2 border-r-2 border-[#eee] pr-3 ml-10 cursor-pointer">
            <img src="/Img/nav/woman.png" alt="" class="w-[40px] h-[40px] cursor-pointer">
            <div class="flex flex-col gap-[2px] text-sm">
                <span class="font-bold text-[#072635]">Dr.Jose Simmons</span>
                <span class="text-[#707070] text-[12px]">General practicioner</span>
            </div>
        </div>

          <!--Settings button-->
        <div class="flex justify-between items-center gap-2 px-5 py-5 ml-[-5px] cursor-pointer">
            <img src="/Img/nav/setting.png" alt="" class="w-[18px]">
            <img src="/Img/nav/more.png" alt="" class="w-[4px]">
        </div>
    </nav>
</template>

<script setup>
const navItem = ref([
    {
        img: '/Img/nav/home.png',
        content: "Overview"
    },
    {
        img: '/Img/nav/group.png',
        content: "Patients"
    },
    {
        img: '/Img/nav/calendar.png',
        content: "Schedule"
    },
    {
        img: '/Img/nav/chat.png',
        content: "Message"
    },
    {
        img: '/Img/nav/credit_card.png',
        content: "Transactions"
    }
])
</script>

<style lang="scss" scoped></style>