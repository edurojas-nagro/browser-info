<template>
  <div class="container">
     <h2>
        Coordernadas (geolocation)
    </h2>
    <hr>
    <div class="row">
        <div class="col-md-4 areaImg">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQsa6UO25ZH3YRLLvalIJmVpJ18U-VUGtHeMIEyYl9oXZ_WcppwJga2Onlyo8wST9OuueE&usqp=CAU" alt="coord" class="img-fluid iconeImg">
        </div>
        <div class="col-md-8">
             <table class="table table-hover">
                <thead>
                    <th>Attributes</th>
                    <th>Valores</th>
                </thead>
                <tbody>
                    <tr>
                        <td>
                            <b>latitude</b>
                        </td>
                        <td class="lead" style="font-size: 23px;">
                            {{lati}}
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <b>Longitude</b>
                        </td>
                        <td class="lead" style="font-size: 23px;">
                            {{long}}
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
    name: "coordenadas",
    data(){
        return {
            lati: null,
            long: null
        }
    },
    methods:{
        getLocation(){
            if(process.server) {return;}
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(this.showPosition);
            } else {
                console.log("Geolocation is not supported by this browser.")
            }

        },

        showPosition(position) {
            console.log("Latitude: " + position.coords.latitude)
            console.log("Longitude: " + position.coords.longitude)
            this.lati = position.coords.latitude
            this.long = position.coords.longitude

        },
    },
    created(){
        this.getLocation()
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
    width: 100px !important;
    height: 100px !important;
    display: block;
}
</style>