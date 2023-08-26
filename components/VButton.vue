<script setup>
defineProps(['id','icon','color'])
</script>

<template lang="">
     <button 
          class="text-white py-2 px-4 rounded-sm h-[55px] w-[125px] "
          @click=""
          :style="{ backgroundColor: color}"
          :id= "id"
          >
        {{id }}
     </button>

     
</template>