<script setup>
    import AuthenticatedLayout from '@/layouts/AuthenticatedLayout.vue'
</script>

<template>
    <AuthenticatedLayout :routeTitle="currentRouteName">
        <h1>Exemplos</h1>
    </AuthenticatedLayout>
</template>

<style lang="scss" scoped>
    @import '@/assets/scss/_main';
</style>

<script>
    export default {
        computed: {
            currentRouteName() {
                return this.$route.meta.title
            },
        },
    }
</script>