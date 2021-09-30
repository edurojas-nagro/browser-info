<template>
    <div class="">
        
        <nav class="sb-topnav navbar navbar-expand navbar-dark bg-dark">
            <!-- Navbar Brand-->
            <NuxtLink  to='/' class="navbar-brand ps-3">
                Browser Info
            </NuxtLink >
            <!-- Sidebar Toggle-->
            <button class="btn btn-link btn-sm order-1 order-lg-0 me-4 me-lg-0" id="sidebarToggle" href="#!">
                <!-- <i class="fas fa-bars"></i> -->
                <img src="@/assets/img/menu.png" alt="" class="img-fluid" width="25">
            </button>
        </nav>
        <div id="layoutSidenav">
            <div id="layoutSidenav_nav">
                <nav class="sb-sidenav accordion sb-sidenav-dark" id="sidenavAccordion">
                    <div class="sb-sidenav-menu">
                        <div class="nav">
                            <div class="sb-sidenav-menu-heading">Core</div>
                            <NuxtLink class="nav-link" to="/">
                                <div class="sb-nav-link-icon"><i class="fas fa-tachometer-alt"></i></div>
                                Dashboard
                            </NuxtLink>                          
                        </div>
                    </div>
                    <div class="sb-sidenav-footer">
                        <div class="small">Nagro System</div>
                        Browser Info
                    </div>
                </nav>
            </div>
            <div id="layoutSidenav_content">
                <main>
                    <div class="container-fluid px-4 pb-5">
                        <h1 class="mt-4">Informações</h1>
                        <ol class="breadcrumb mb-4">
                            <li class="breadcrumb-item active">Browser</li>
                        </ol>

                        <div class="container-fluid">                            
                            <dadosSystem></dadosSystem>
                            <br>
                            <dadosTela></dadosTela>
                            <coordenadas></coordenadas>
                        </div>                       
                    </div>
                </main>
            </div>
        </div>

    </div>
</template>
<script>
import "@/assets/css/styles.css"
import "../node_modules/fontawesome"
import "bootstrap/dist/css/bootstrap.min.css"
import dadosTela from "../components/dadosTela.vue"
import dadosSystem from "../components/dadosSystem.vue"
import coordenadas from "../components/coodernadas.vue"
export default {
    components:{
        dadosTela,
        dadosSystem,
        coordenadas
    },
    data(){
        return {
            informacoes: '',
            imgSO: '@/assets/img/windows.png'
        }
    },
    
    mounted(){
        if(process.server) {return;}
        window.addEventListener('DOMContentLoaded', event => {

            // Toggle the side navigation
            const sidebarToggle = document.body.querySelector('#sidebarToggle');
            if (sidebarToggle) {
                // Uncomment Below to persist sidebar toggle between refreshes
                // if (localStorage.getItem('sb|sidebar-toggle') === 'true') {
                //     document.body.classList.toggle('sb-sidenav-toggled');
                // }
                sidebarToggle.addEventListener('click', event => {
                    event.preventDefault();
                    document.body.classList.toggle('sb-sidenav-toggled');
                    localStorage.setItem('sb|sidebar-toggle', document.body.classList.contains('sb-sidenav-toggled'));
                });
            }

        });
        
        // navigator.userAgentData.platform

    }
}
</script>
<style scoped>
body{
    background-color: #F9F9F9 !important;
}
.bg-primary{
    background-color: #0065BD !important;
}
</style>