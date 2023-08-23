<script>
import { Icon } from '@iconify/vue';
export default {
    components: {
		Icon,
	},
}
</script>
<template>
    <div class="border w-100 flex justify-between items-center p-4">
        <img class="w-[190px]" src="/img/logo.png" alt="logo">
        <nav class="flex justify-between w-[40%]">
        <ul class="flex gap-16 items-stretch">
            <li><NuxtLink to="/">Home</NuxtLink></li>
            <li><NuxtLink to="/accounts">Accounts</NuxtLink></li>
            <li><NuxtLink to="/sales"> Sales</NuxtLink></li>
        </ul>
        <ul class="flex gap-8">
            <li><Icon icon="ph:user" /></li>
            <li><Icon icon="ant-design:message-outlined" /></li>
            <li><Icon icon="mdi:bell-outline" /></li>
        </ul>
        
       
        </nav>
    </div>
</template>

<style scoped>
    .router-link-active{
        padding-bottom: 24px;
        border-bottom: 4px solid red;
    }
</style>
