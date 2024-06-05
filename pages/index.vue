<template>
     <main class="flex gap-8 justify-between">
      <div class="flex flex-col  h-[947px] justify-evenly  mt-[10px]">
         <div class="bg-white h-[690px] w-[600px] rounded-2xl mt-[20px]">
          <Diagnosis />
         </div>
         <div class="bg-white h-[295px] w-[600px] rounded-2xl px-4 py-4 mt-12">
            <DiagnosisList />
         </div>
      </div>

      <div class="flex flex-col gap-4">
         <div class="bg-white h-[730px] w-[350px] rounded-2xl">
            <jessica />
         </div>
         <div class="bg-white h-[195px] w-[350px] rounded-2xl mt-4">
            <Lab />
         </div>
      </div>
   </main>
</template>

<script setup>

</script>

<style lang="scss" scoped>

</style>