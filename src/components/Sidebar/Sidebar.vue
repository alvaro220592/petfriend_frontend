<script setup>
    import { useUsers } from '@/stores/user'

    const store = useUsers()

    // onBeforeMount(() => {
    //     if (!store.hasUserData) {
    //         store.getData()
    //     }
    // })

    const submitLogout = () => {
        store.logout()
    }
</script>
<template>
    <aside id="sidebar">
        <div class="logo__text">
            <h1>PetFriend</h1>
        </div>
        <ul class="menu_list">

            <li class="menu">
                <router-link class="router-link" to="/dashboard">
                    <i class="bi bi-graph-up-arrow"></i>
                    <span>Dashboard</span>
                </router-link>
            </li>

            <li class="menu">
                <router-link class="router-link" to="/schedule">
                    <i class="bi bi-calendar-week"></i>
                    <span>Agenda</span>
                </router-link>
            </li>

            <li class="menu">
                <router-link class="router-link" to="" @click="expandMenu($event)">
                    <i class="bi bi-plus-circle-fill"></i>
                    <span>Cadastro</span>
                </router-link>
                <ul class="submenu_list hide">
                    <li class="submenu">
                        <i class="bi bi-chevron-right"></i><span>Clientes</span>
                    </li>
                    <li class="submenu">
                        <i class="bi bi-chevron-right"></i><span>Pets</span>
                    </li>
                    <li class="submenu">
                        <i class="bi bi-chevron-right"></i><span>Usuários</span>
                    </li>
                </ul>
            </li>

            <li class="menu" title="Sair">
                <router-link class="router-link" to="" @click="submitLogout()">
                    <i class="bi bi-door-open"></i>
                    <span>Sair</span>
                </router-link>
            </li>
        </ul>
    </aside>
</template>

<script>
export default {
    name: 'Sidebar',

    mounted() {
        if(localStorage.getItem('sidebarExpanded')) {
            document.getElementById('sidebar').classList.add('expanded')
            localStorage.removeItem('sidebarExpanded');
        }

        document.querySelectorAll('.menu').forEach(menu => {
            if(menu.querySelector('.router-link > span').innerText.toLowerCase() != 'sair') {
                menu.addEventListener('mouseover', () => {
                    document.getElementById('sidebar').classList.add('expanded')
                    
                    if(!localStorage.getItem('sidebarExpanded')) {
                        localStorage.setItem('sidebarExpanded', 'sidebarExpanded');
                    }
                })
            }
        })
    },

    methods: {
        expandMenu: event => {
            event.currentTarget.parentNode
                .querySelector('.submenu_list')
                .classList.toggle('hide')
        },
    },
}
</script>

<style lang="scss" src="./style.scss">
</style>