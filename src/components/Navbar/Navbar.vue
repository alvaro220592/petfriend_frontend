<template>
    <nav id="navbar">
        <span @click="sidebarToggle">
            <i class="bi bi-list menu_button"></i>
        </span>
    </nav>
</template>

<script>
export default {
    name: 'Navbar',

    methods: {
        sidebarToggle: () => {
            let sidebar = document.getElementById('sidebar')

            sidebar.classList.toggle('expanded')

            if(sidebar.classList.contains('expanded')) {
                if(!localStorage.getItem('sidebarExpanded')) {
                    localStorage.setItem('sidebarExpanded', 'sidebarExpanded');
                }
            }else {
                if(localStorage.getItem('sidebarExpanded')) {
                    localStorage.removeItem('sidebarExpanded');
                }
            }
        },
    },
}
</script>

<style lang="scss" src="./style.scss">

</style>