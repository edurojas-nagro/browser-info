<template>
  <div class="container">
    <div class="row">
        <div class="col-md-4 col-4 text-center" v-for="dado in systemDados" :key='dado'>
            <div v-if="dado.dado == 'SO'">
                <img
                    :src="dado.desc == 'Windows' ? dado.imgWindow : dado.imgLinux"
                    alt="typeScreen"
                    class="img-fluid"
                    width="50%"
                />
                <p>
                    <b>{{dado.desc}}</b>
                </p>
            </div>
            <div v-else>
                <img
                    :src="dado.desc == 'Google Chrome' ? dado.imgChrome : dado.imgEdge"
                    alt="typeScreen"
                    class="img-fluid"
                    :width="dado.desc == 'Google Chrome' ? '50%' : '100%'"
                />
                <p>
                    <b>{{dado.desc}}</b>
                </p>
            </div>            
        </div>
        <div class="col-md-4 col-4 text-center" style="display: flex; align-items: center; justify-content: center;">
            <h1>Version: {{versao}}</h1>
        </div>
    </div>
  </div>
</template>
<script>
import "@/assets/css/styles.css";
import "../node_modules/fontawesome";
import "bootstrap/dist/css/bootstrap.min.css";
export default {
    name: "dadosSystem",
    data(){
        return {
            systemDados: [],
            caminhoImg: "",
            versao: ""
        }
    },
    methods:{
        getDADOS(){
            if(process.server) {return;}
            this.systemDados.push(
                {   
                    dado: 'SO', 
                    desc: navigator.userAgentData.platform,
                    imgWindow: 'https://amiunique.org/summary/windows.png',
                    imgLinux: 'https://amiunique.org/summary/linux.png'
                },
                
                {   
                    dado: 'Navegador', 
                    desc: navigator.userAgentData.brands[1].brand,
                    imgFirefox: 'https://amiunique.org/summary/firefox.png',
                    imgChrome: 'https://amiunique.org/summary/chrome.png',
                    imgEdge: 'https://mundoconectado.com.br/uploads/chamadas/microsoft-edge-logo-novo-chamada.jpg'

                },
            )
            
            console.log(this.systemDados[0])
            if(this.systemDados[0].desc == 'Android' && window.screen.width <= 800){
                this.systemDados[0].imgLinux = 'https://cdn.icon-icons.com/icons2/2235/PNG/512/android_os_logo_icon_134673.png'
            }

            console.log(navigator.userAgentData.brands[1].brand)
        },

        getVersionBrowser(){
            return this.versao = navigator.userAgentData.brands[1].version
        },
    },
    created(){
        if(process.server) {return;}
        this.getDADOS()
        this.getVersionBrowser()
    }
};
</script>