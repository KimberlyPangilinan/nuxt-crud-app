<script setup>
defineProps(['id','placeholder', 'type','isRequired','modelValue'])
defineEmits(['update:modelValue'])
</script>

<template lang="">
    <div class="grow">
        <label class="block">
            <span class="after:content-['*'] after:ml-0.5 after:text-red-500 block text-sm font-medium text-slate-700">
                {{id}}
            </span>
            <input
                type={{type}}
                name={{id}}
                :value="modelValue"
                @input="$emit('update:modelValue', $event.target.value)"
                class="px-3 py-2 bg-white border shadow-sm border-slate-300 placeholder-slate-400 h-[46px] rounded-sm focus:outline-none focus:border-red-200 focus:ring-red-200 block w-full  sm:text-sm focus:ring-1" 
                 />
         </label>
    </div>
</template>