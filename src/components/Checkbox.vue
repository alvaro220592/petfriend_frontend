<script setup>
import { computed } from 'vue'

const emit = defineEmits(['update:checked'])

const props = defineProps({
    checked: {
        type: [Array, Boolean],
        default: false,
    },
    value: {
        default: null,
    },
})

const proxyChecked = computed({
    get() {
        return props.checked
    },

    set(val) {
        emit('update:checked', val)
    },
})
</script>

<template>
    <input
        type="checkbox"
        :value="value"
        v-model="proxyChecked"
        class="rememberme" />
</template>

<style lang="scss" scoped>

    @import '@/assets/scss/_main';

    .rememberme {
        background-color: $laranja;
        color: $laranja;
        border-radius: 10px;
        border: 1px solid $abobora;
    }

    .rememberme:focus {
        border: 1px solid $abobora;
        border-radius: 10px;
        --tw-ring-color: none;
    }

    .rememberme:checked {
        border: 1px solid $abobora;
        border-radius: 10px;
        --tw-ring-color: none;
        background-image: url("data:image/svg+xml,%3csvg viewBox='0 0 16 16' fill='fff' xmlns='http://www.w3.org/2000/svg'%3e%3cpath d='M12.207 4.793a1 1 0 010 1.414l-5 5a1 1 0 01-1.414 0l-2-2a1 1 0 011.414-1.414L6.5 9.086l4.293-4.293a1 1 0 011.414 0z'/%3e%3c/svg%3e")
    }
</style>