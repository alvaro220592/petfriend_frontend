<script setup>
import { ref, onBeforeMount } from 'vue'
import { useUsers } from '@/stores/user'
import ApplicationLogo from '@/components/ApplicationLogo.vue'
import Dropdown from '@/components/Dropdown.vue'
import DropdownLink from '@/components/DropdownLink.vue'
import NavLink from '@/components/NavLink.vue'
import ResponsiveNavLink from '@/components/ResponsiveNavLink.vue'
import Sidebar from '@/components/Sidebar/Sidebar.vue'
import Navbar from '@/components/Navbar/Navbar.vue'

const showingNavigationDropdown = ref(false)

const store = useUsers()

const auth = store.authUser

onBeforeMount(() => {
    if (!store.hasUserData) {
        store.getData()
    }
})

const submitLogout = () => {
    store.logout()
}
</script>

<template>
    <div v-if="auth">
        <section class="conteudo">
            <Sidebar />

            <aside class="rightSide">
                <Navbar />

                <!-- Page Content -->
                <main>
                    <div class="pagina">
                        <p class="breadcrumbs"><span>Início > {{ routeTitle }}</span></p>

                        <div class="main_card">
                            <slot />
                        </div>
                    </div>
                </main>
            </aside>
        </section>
    </div>
</template>

<script>
export default {
    mounted() {},

    props: {
        routeTitle: String
    },

    methods: {},
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_main';

@media screen and (max-width: 760px) {
    // Parte da página que não é a sidebar
    .rightSide {
        margin-left: $xsNotExpandedSidebarWidth;
    }
}

@media screen and (max-width: 991px) {
    .rightSide {
        margin-left: $smNotExpandedSidebarWidth;
    }
}

@media screen and (max-width: 1199px) {
    .rightSide {
        margin-left: $mdNotExpandedSidebarWidth;
    }
}

// Tela grande
@media screen and (min-width: 1200px) {
    .rightSide {
        margin-left: $lgNotExpandedSidebarWidth;
    }
}

// Padrão
.conteudo {
    background-color: $pastel;
    min-height: 100vh;
    display: flex;

    .rightSide {
        width: 100%;

        main {
            background-color: $turquesa;
            min-height: 100vh;
        }
    }
}

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