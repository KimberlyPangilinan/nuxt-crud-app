<template>
    <div>
        <img src="/logo.png" alt="logo">
        <nav>
        <ul>
            <li><NuxtLink to="/">Home</NuxtLink></li>
            <li><NuxtLink to="/accounts">Accounts</NuxtLink></li>
            <li><NuxtLink to="/"> Sales</NuxtLink></li>
        </ul>
        </nav>
    </div>
</template>

<style scoped>
    .router-link-active{
        border-bottom: 2px solid red;
    }
</style>
