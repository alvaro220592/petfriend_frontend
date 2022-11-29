<script setup>
import { ref, onBeforeMount } from 'vue'
import { useUsers } from '@/stores/user'
import ApplicationLogo from '@/components/ApplicationLogo.vue'
import Dropdown from '@/components/Dropdown.vue'
import DropdownLink from '@/components/DropdownLink.vue'
import NavLink from '@/components/NavLink.vue'
import ResponsiveNavLink from '@/components/ResponsiveNavLink.vue'

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
            <aside id="sidebar">side</aside>

            <aside class="rightSide">
                <nav id="navbar">
                    <span @click="sidebarToggle">click</span>
                </nav>
                <!-- Page Content -->
                <main>
                    <slot />
                </main>
            </aside>
        </section>
    </div>
</template>

<script>
export default {
    mounted() {},

    methods: {
        sidebarToggle: () => {
            let sidebar = document.getElementById('sidebar')

            sidebar.classList.toggle('expanded')
        },
    },
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_main';

// xs (for phones - screens less than 768px wide)
// sm (for tablets - screens equal to or greater than 768px wide)
// md (for small laptops - screens equal to or greater than 992px wide)
// lg (for laptops and desktops - screens equal to or greater than 1200px wide)

// Mobile
@media screen and (max-width: 760px) {
    $xsNotExpandedSidebarWidth: 50px;
    $xsExpandedSidebarWidth: 150px;

    .conteudo {
        #sidebar:not(.expanded),
        #sidebar.expanded + .rightSide,
        #sidebar:not(.expanded) + .rightSide,
        .expanded {
            transition: $transition;
        }

        // Sidebar sem a classe expanded
        #sidebar:not(.expanded) {
            width: $xsNotExpandedSidebarWidth;
        }

        // Conteúdo interno (o símbolo + indica um elemento próximo)
        #sidebar.expanded + .rightSide {
            margin-left: $xsExpandedSidebarWidth;
        }

        .expanded {
            width: $xsExpandedSidebarWidth;
        }

        // Parte da página que não é a sidebar
        .rightSide {
            margin-left: $xsNotExpandedSidebarWidth;

            main {
                margin: 0px 10px;
            }
        }
    }
}

@media screen and (max-width: 991px) {
    $smNotExpandedSidebarWidth: 50px;
    $smExpandedSidebarWidth: 150px;

    #sidebar:not(.expanded),
    #sidebar.expanded + .rightSide,
    #sidebar:not(.expanded) + .rightSide,
    .expanded {
        transition: $transition;
    }

    .conteudo {
        #sidebar:not(.expanded) {
            width: $smNotExpandedSidebarWidth;
        }

        #sidebar.expanded + .rightSide {
            margin-left: $smExpandedSidebarWidth;
        }

        .expanded {
            width: $smExpandedSidebarWidth;
        }

        .rightSide {
            margin-left: $smNotExpandedSidebarWidth;
        }
    }
}

@media screen and (max-width: 1199px) {
    $mdNotExpandedSidebarWidth: 50px;
    $mdExpandedSidebarWidth: 200px;

    #sidebar:not(.expanded),
    #sidebar.expanded + .rightSide,
    #sidebar:not(.expanded) + .rightSide,
    .expanded {
        transition: $transition;
    }

    .conteudo {
        #sidebar:not(.expanded) {
            width: $mdNotExpandedSidebarWidth;
        }

        #sidebar.expanded + .rightSide {
            margin-left: $mdExpandedSidebarWidth;
        }

        .expanded {
            width: $mdExpandedSidebarWidth;
        }

        .rightSide {
            margin-left: $mdNotExpandedSidebarWidth;
        }
    }
}

// Tela grande
@media screen and (min-width: 1200px) {
    $lgNotExpandedSidebarWidth: 50px;
    $lgExpandedSidebarWidth: 200px;

    #sidebar:not(.expanded),
    #sidebar.expanded + .rightSide,
    #sidebar:not(.expanded) + .rightSide,
    .expanded {
        transition: $transition;
    }

    .conteudo {
        #sidebar:not(.expanded) {
            width: $lgNotExpandedSidebarWidth;
        }

        #sidebar.expanded + .rightSide {
            margin-left: $lgExpandedSidebarWidth;
        }

        .expanded {
            width: $lgExpandedSidebarWidth;
        }

        .rightSide {
            margin-left: $lgNotExpandedSidebarWidth;
        }
    }
}

// Padrão
.conteudo {
    background-color: $pastel;
    min-height: 100vh;
    display: flex;
    overflow: scroll;

    #sidebar {
        min-height: 100vh;
        background-color: $pastel;
        position: fixed;
    }

    .rightSide {
        width: 100%;

        #navbar {
            background-color: $laranja;
        }

        main {
            background-color: $turquesa;
            min-height: 100vh;
        }
    }
}
</style>