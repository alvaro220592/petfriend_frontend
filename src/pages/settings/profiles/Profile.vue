<script setup>
    import AuthenticatedLayout from '@/layouts/AuthenticatedLayout.vue'
</script>

<template>
    <AuthenticatedLayout :routeTitle="currentRouteName">
        PROFILEEEEEE
    </AuthenticatedLayout>
</template>

<script>
    export default {
        name: 'Profile',

        computed: {
            currentRouteName() {
                return this.$route.meta.title
            }
        }
    }
</script>