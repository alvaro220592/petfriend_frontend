<script setup>
    import AuthenticatedLayout from '@/layouts/AuthenticatedLayout.vue'
</script>

<template>
    <AuthenticatedLayout :routeTitle="currentRouteName">
        <h1>Agenda</h1>
    </AuthenticatedLayout>
</template>

<style lang="scss" scoped>
    
    @import '@/assets/scss/_main';

    .pagina {
        padding: 10px 0px;

        .main_card {
            background-color: $palido;
            padding: 20px;
            border: 1px solid $laranja;
            border-radius: 4px;
            margin: 0px 10px;
        }
    }

</style>

<script>
    export default {
        computed: {
            currentRouteName() {
                return this.$route.meta.title
            }
        }
    }
</script>