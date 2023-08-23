<script setup>
defineProps(['title','pic', 'desc'])
</script>


<template>
    <div class="grid place-items-center gap-4">
        <img class="w-[110px]" :src="pic" alt=""/>
        <h4 class="text-lg">{{ title }}</h4>
        <p class="text-base font-medium w-8/12">{{ desc  }}</p>
    </div>
</template>