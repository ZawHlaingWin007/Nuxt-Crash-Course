<template>
    <div class="p-10">
        <div class="p-4 bg-gray-100 rounded">
            <img
                :src="yesNoData.image"
                :alt="yesNoData.answer"
                class="object-cover w-20 h-20 rounded-md"
            >
            <p>Answer - {{ yesNoData.answer }}</p>
        </div>
        <ul class="flex flex-wrap gap-4 my-4">
            <li
                v-for="pokemon in pokemonData.results"
                class="cursor-pointer"
            >
                <p class="inline-block p-2 font-serif text-sm capitalize rounded bg-cyan-100 text-cyan-400">{{
                    pokemon.name }}</p>
            </li>
        </ul>

        <ul class="grid grid-cols-3 gap-10">
            <template v-for="product in products">
                <ProductCard :product="product" />
            </template>
        </ul>
    </div>
</template>

<script setup lang="ts">
const { data: yesNoData }: any = await useFetch('https://yesno.wtf/api')
const { data: pokemonData }: any = await useFetch('https://pokeapi.co/api/v2/pokemon');
const { data: products } = await useFetch('https://fakestoreapi.com/products');

console.log("Pokemon", pokemonData.value)
console.log("YesNo", yesNoData.value)
console.log("Products", products)
</script>

<style scoped></style>