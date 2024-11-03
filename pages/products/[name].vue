<template>
    <div>
        Product Name - {{ name }}
    </div>
</template>

<script setup lang="ts">
const { name } = useRoute().params;
</script>

<style scoped></style>