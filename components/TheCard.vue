<script setup>
defineProps(['title','pic', 'desc'])
</script>


<template>
    <div>
        <h4>{{ title }}</h4>
        <img :src="pic" alt=""/>
        <p>{{ desc  }}</p>
    </div>
  
</template>