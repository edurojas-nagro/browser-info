<template>
  <div class="container">
    <h2>
        Dados de sua Tela
    </h2>
    <hr>
    <div class="row">
        <div class="col-md-4 col-12 areaImg">
            <img
            :src="caminhoImg"
            alt="typeScreen"
            class="img-fluid iconeImg"
            />
        </div>
        <div class="col-md-8 col-12">
            <table class="table table-hover">
                <thead>
                    <th>Attributes</th>
                    <th>Valores</th>
                </thead>
                <tbody>
                    <tr v-for="dado in screenDados" :key='dado'>
                        <td>
                            <b>{{dado.dado}}</b>
                        </td>
                        <td class="lead" style="font-size: 23px;">
                            {{dado.desc}}
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
  </div>
</template>
<script>
import "@/assets/css/styles.css";
import "../node_modules/fontawesome";
import "bootstrap/dist/css/bootstrap.min.css";
export default {
    name: "dadosTela",
    data(){
        return {
            screenDados: [],
            caminhoImg: "",
            imgPC: 'https://i.pinimg.com/736x/f7/f5/86/f7f5860b66c2f895eb24d78d6968b926.jpg',
            // imgPC: 'https://cdn.dribbble.com/users/42460/screenshots/5374328/icon_computer_2.gif',
            imgMobile: 'https://cdn2.iconfinder.com/data/icons/mobile-phone-34/100/touch-screen-3-mobile-phone-interactions-smartphone-front-tap-screen-finger-hand-512.png'
        }
    },
    methods:{
        getDADOS(){
            if(process.server) {return;}
            this.screenDados.push(
                {dado: 'largura', desc: window.screen.width},
                {dado: 'altura', desc: window.screen.height},
                {dado: 'AvalWidth', desc: window.screen.availWidth},
                {dado: 'AvalHeigth', desc: window.screen.availHeight},
                {dado: 'Color Depth', desc: window.screen.colorDepth},
                {dado: 'Pixel Depth', desc: window.screen.pixelDepth}
            )

            if(this.screenDados[0].desc <= 800){
                this.caminhoImg = this.imgMobile
            }else{
                 this.caminhoImg = this.imgPC
            }
        }
        
    },
    created(){
        if(process.server) {return;}
        this.getDADOS()
    }
};
</script>
<style scoped>
.areaImg{
    display: flex;
    justify-content: center;
    align-items: center;
}
.iconeImg{
    width: 200px !important;
    height: 200px !important;
    display: block;
}
</style>