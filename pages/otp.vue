<script setup>
const data = ref(null);
</script>

<template>
    <section class="">
        <h2 class="mb-4 text-center text-gray-500">Enter Verification Code</h2>
        <div class="w-[300px] mx-auto bg-white rounded-xl p-5 border">
            <OTPInput
                v-model="data"
                :fields="5"
            ></OTPInput>
        </div>
        <div class="pt-5 text-center text-gray-500">{{ data }}</div>
    </section>
</template>

<!-- 12345 -->
