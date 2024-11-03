<template>
    <nav class="container m-4">
        <ul class="flex items-center gap-4">
            <li class="px-3 py-2 font-serif text-purple-400 bg-purple-100 rounded">
                <NuxtLink to="/">Home</NuxtLink>
            </li>
            <li class="px-3 py-2 font-serif text-purple-400 bg-purple-100 rounded">
                <NuxtLink to="/products">Products</NuxtLink>
            </li>
            <li class="px-3 py-2 font-serif text-purple-400 bg-purple-100 rounded">
                <NuxtLink to="/otp">Otp</NuxtLink>
            </li>
        </ul>
    </nav>
    <slot />
</template>

<script setup lang="ts">

</script>

<style scoped>
.router-link-exact-active {
    color: cyan;
}
</style>