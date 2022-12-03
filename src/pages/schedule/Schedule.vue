<script setup>
import AuthenticatedLayout from '@/layouts/AuthenticatedLayout.vue'
</script>

<template>
    <AuthenticatedLayout>
            <div class="pagina">

                <p class="breadcrumbs"><span>Início > Teste</span></p>
                
                <div class="main_card">
                    <h1>Agenda</h1>
                </div>
            </div>
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
