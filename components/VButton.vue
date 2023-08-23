<script setup>
defineProps(['id','icon','color'])
</script>

<template lang="">
     <button 
          class="text-white py-2 px-4 rounded-sm "
          @click=""
          :style="{ backgroundColor: color}"
          id="new"
          >
        {{id }}
     </button>

     
</template>