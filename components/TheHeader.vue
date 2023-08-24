<script>
import { Icon } from '@iconify/vue';
export default {
    components: {
		Icon,
	},
}
</script>
<template>
    <div class="fixed top-0 w-screen flex-col border w-100 flex bg-white justify-between items-center p-4 md:flex-row z-[100] ">
        <img class="w-[190px]" src="/img/logo.png" alt="logo">
        <nav class="flex flex-col-reverse justify-between w-[34%] sm:flex-row">
            <ul class="flex gap-16 items-stretch">
                <li><NuxtLink to="/" class="min-w-[400px]">Home</NuxtLink></li>
                <li><NuxtLink to="/accounts">Accounts</NuxtLink></li>
                <li><NuxtLink to="/sales"> Sales</NuxtLink></li>
            </ul>
            <ul class="hidden gap-8 md:flex">
                <li><Icon icon="ph:user" /></li>
                <li><Icon icon="ant-design:message-outlined" /></li>
                <li><Icon icon="mdi:bell-outline" /></li>
            </ul>
        </nav>
    </div>
</template>

<style scoped>
    .router-link-active{
        padding-bottom: 25px;
        border-bottom: 7px solid red;
    }
    
</style>
