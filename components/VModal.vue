<template>
    <div class="fixed inset-0 flex items-center justify-center">
      <div class="flex flex-col gap-8 absolute top-[50%] left-[50%] transform translate-x-[-50%] translate-y-[-50%] p-16 border-t-4  rounded-md bg-white shadow-md" :style="{ borderColor: color}">
        <div class="flex gap-4">
          <img :src="img" alt="" class="object-cover w-[60px] h-[50px]" />
          <div>
            <h4 class="font-bold mb-4">{{ title }}</h4>
            <p class="w-[227px] text-xs">
             {{ subtitle }}
            </p>
          </div>
        </div>
        <div class="flex gap-8 justify-center">
          <button class="w-[91px] h-[46px] rounded-sm text-white bg-[#D9D9D9]" @click="closeModal">Cancel</button>
          <button class="w-[91px] h-[46px] rounded-sm text-white" :style="{ backgroundColor: color}" @click="handleClick">{{ name }}</button>
        </div>
      </div>
    </div>
  </template>
  
<script setup>
    import { ref, defineEmits } from 'vue';
    
    defineProps(['title','subtitle', 'img','color','name'])
    const emit = defineEmits();
    const closeModal = () => {
        emit('close-modal');
    };
    const handleClick = () => {
        emit('handle-click');
    };
</script>