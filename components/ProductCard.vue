<template>
    <NuxtLink
        :to="`/products/${product.title}`"
        class="flex h-full p-4 font-serif bg-gray-100 rounded"
    >
        <div class="w-40">
            <img
                :src="product.image"
                :alt="product.title"
                class="object-contain w-full h-40 rounded-lg"
                loading="lazy"
            />
        </div>
        <form class="flex-auto p-6">
            <div class="flex flex-wrap items-baseline">
                <h1 class="flex-none w-full mb-3 text-2xl leading-none text-slate-900">
                    {{ product.title }}
                </h1>
                <div class="flex-auto text-lg font-medium text-slate-500">
                    ${{ product.price }}
                </div>
                <div class="px-2 py-1 text-xs leading-6 text-green-500 uppercase bg-green-100 rounded">
                    {{ product.category }}
                </div>
            </div>
            <p class="text-sm text-slate-500">
                Free shipping on all continental US orders.
            </p>
        </form>
    </NuxtLink>
</template>

<script setup lang="ts">
defineProps(['product'])
</script>

<style scoped></style>