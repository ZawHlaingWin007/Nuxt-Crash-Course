<script lang="ts" setup>
import { ref, watch } from 'vue';

const props = defineProps<{
    fields: number;
}>();

// 'data' should hold an array of strings, initialized with empty strings based on 'fields'
const data = ref<string[]>(Array(props.fields).fill(''));

// Typing for 'firstInputEl' as an array of HTMLInputElement refs
const firstInputEl = ref<HTMLInputElement[]>([]);

const emit = defineEmits(['update:modelValue']);

// Watch for changes in the data array
watch(
    () => data.value,
    (newVal) => {
        if (
            newVal.join('') !== '' &&
            newVal.length === props.fields &&
            !newVal.includes('')
        ) {
            emit('update:modelValue', Number(newVal.join('')));
        } else {
            emit('update:modelValue', null);
        }
    },
    { deep: true }
);

// Use general Event type for compatibility with Vue template
const handleOtpInput = (e: Event) => {
    const target = e.target as HTMLInputElement;
    if (target.value && target.nextElementSibling) {
        (target.nextElementSibling as HTMLInputElement).focus();
    } else if (!target.value && target.previousElementSibling) {
        (target.previousElementSibling as HTMLInputElement).focus();
    }
};

// Typing for the paste event as ClipboardEvent
const handlePaste = (e: ClipboardEvent) => {
    const pasteData = e.clipboardData?.getData('text') || '';
    let nextEl = firstInputEl.value[0]?.nextElementSibling as HTMLInputElement | null;
    for (let i = 1; i < pasteData.length; i++) {
        if (nextEl) {
            data.value[i] = pasteData[i];
            nextEl = nextEl.nextElementSibling as HTMLInputElement | null;
        }
    }
};
</script>

<template>
    <div
        class="flex justify-around w-full otp"
        @input="handleOtpInput"
    >
        <template
            v-for="field in fields"
            :key="field"
        >
            <input
                v-model="data[field - 1]"
                ref="firstInputEl"
                type="text"
                maxlength="1"
                class="w-10 h-10 text-center border rounded"
                @paste="field === 1 && handlePaste($event)"
            />
        </template>
    </div>
</template>
