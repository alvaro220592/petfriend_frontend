<script setup>
import { onMounted, ref } from 'vue'

defineProps(['modelValue'])

defineEmits(['update:modelValue'])

const input = ref(null)

onMounted(() => {
    if (input.value.hasAttribute('autofocus')) {
        input.value.focus()
    }
})
</script>

<template>
    <!-- <input class="border-gray-300 focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50 rounded-md shadow-sm" -->
    <input class="input"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        ref="input" />
</template>

<style lang="scss" scoped>
    
    @import '@/assets/scss/_main';

    .input {
        width: 100%;
        border-radius: 4px;
        border: solid 1px $laranja;
    }

    .input:focus {
        border: solid 2px $turquesa;
        box-shadow: none;
    }

</style>