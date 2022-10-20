<template>
  <div>
    <b-container fluid>
      <Navbar></Navbar>
       <br>  <br>
        <b-jumbotron header="Sesión 4" lead="Momento 1" v-show="!inicio">
          <center>
            <b-img  src="/se1.png" width="210" height="200" alt="Circle image"></b-img>
            <b-img  src="/adolescentes.png" width="210" height="200" alt="Circle image"></b-img>
          </center>
          <p>Tablas de Frecuencia</p>
          <b-button variant="primary" @click="comenzar">Comenzar</b-button>
        </b-jumbotron>

        <b-row v-show="inicio">
          <b-col>
            <TableSesionCuatro></TableSesionCuatro>
          </b-col>
        </b-row>
         <b-row v-show="inicio">
          <b-col>
            <div>
              <br>
            <b-label>Inserta en la tabla de distribución de frecuencia los siguientes valores  </b-label>
            <b-table-simple bordered>
              <b-tr>
                <b-td colspan="3"></b-td>
                <b-td colspan="3">Relativa</b-td>
              </b-tr>
              <b-tr>
                <b-th>Estatura (metros)</b-th>
                <b-th>Frecuencia absoluta </b-th>
                <b-th>Frecuencia absoluta acumulada  </b-th>
                <b-th>Racional  </b-th>
                <b-th>Decimal</b-th>
                <b-th>Porcentaje</b-th>
              </b-tr>
               <b-tr>
                <b-td>Entre 1,35 y 1,39</b-td>
                <b-td>6</b-td>
                <b-td>6</b-td>
                <b-td><b-input v-model="solucion0.opcionrr"  @change="verificar(solucion0.opcionrr, solucion0.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion0.opciondec" @change="verificar(solucion0.opciondec, solucion0.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion0.opcionpor" @change="verificar(solucion0.opcionpor, solucion0.respuestapor)" type="number"></b-input></b-td>
              </b-tr>
              <b-tr>
                <b-td>Entre 1,40 y 1,44</b-td>
                <b-td>7</b-td>
                <b-td>13</b-td>
                <b-td><b-input v-model="solucion1.opcionrr"  @change="verificar(solucion1.opcionrr, solucion1.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion1.opciondec" @change="verificar(solucion1.opciondec, solucion1.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion1.opcionpor" @change="verificar(solucion1.opcionpor, solucion1.respuestapor)" type="number"></b-input></b-td>
              </b-tr>
              <b-tr>
                <b-td>Entre 1,45 y 1,49</b-td>
                 <b-td>13</b-td>
                 <b-td>26</b-td>
                <b-td><b-input v-model="solucion2.opcionrr"  @change="verificar(solucion2.opcionrr, solucion2.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion2.opciondec" @change="verificar(solucion2.opcionfa, solucion2.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion2.opcionpor" @change="verificar(solucion2.opcionfa, solucion2.respuestapor)" type="number"></b-input></b-td>
              </b-tr>
              <b-tr>
                <b-td>Entre 1,50 y 1,54</b-td>
                <b-td>10</b-td>
                <b-td>36</b-td>
                <b-td><b-input v-model="solucion3.opcionrr"  @change="verificar(solucion3.opcionrr, solucion3.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion3.opciondec" @change="verificar(solucion3.opciondec, solucion3.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion3.opcionpor" @change="verificar(solucion3.opcionpor, solucion3.respuestapor)" type="number"></b-input></b-td>
              </b-tr>
              <b-tr>
                <b-td>Entre 1,55 y 1,60</b-td>
                <b-td>3</b-td>
                <b-td>39</b-td>
                <b-td><b-input v-model="solucion4.opcionrr"  @change="verificar(solucion4.opcionrr, solucion4.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion4.opciondec" @change="verificar(solucion4.opciondec, solucion4.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion4.opcionpor" @change="verificar(solucion4.opcionpor, solucion4.respuestapor)" type="number"></b-input></b-td>
              </b-tr>
              <b-tr>
                <b-td>Total</b-td>
                <b-td>39</b-td>
                <b-td></b-td>
                <b-td><b-input v-model="solucion5.opcionrr"  @change="verificar(solucion5.opcionrr, solucion5.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion5.opciondec" @change="verificar(solucion5.opciondec, solucion5.respuestadec)" type="number"></b-input></b-td>
                <b-td></b-td>
              </b-tr>
            </b-table-simple>
             <b-button block variant="success" id="show-btn" @click="showModal">Resultado</b-button>
          </div>
          </b-col>
        </b-row>
        <div>
    <b-modal ref="my-modal" hide-footer title="Puntaje">
      <div class="d-block text-center">
        <h2>Resultado</h2>
        <h3>Puntos Obtenidos {{ puntos }}</h3>
          <b-img v-if="(puntos>=0 && puntos<=10 )" width="80" height="80" src="/bronce.gif" rounded="circle" alt="Circle image"></b-img>
          <b-img v-if="(puntos>=11 && puntos<=20 )" width="80" height="80" src="/plata.gif" rounded="circle" alt="Circle image"></b-img>
          <b-img v-if="puntos==21" src="/oro.gif" width="80" height="80" rounded="circle" alt="Circle image"></b-img>
      </div>
      <b-button class="mt-3" variant="outline-danger" block @click="hideModal">Nuevo Intento</b-button>
    </b-modal>
  </div>

    </b-container>
  </div>
</template>
<script>
export default {
  data(){
    return{
      inicio:false,
      puntos:0,
      solucion0:{
          respuestarr:'6/39',
          opcionrr:'',
          respuestadec:'0.15',
          opciondec:'',
          respuestapor:'15',
          opcionpor:'',
      },
      solucion1:{
          respuestarr:'7/39',
          opcionrr:'',
          respuestadec:'0.17',
          opciondec:'',
          respuestapor:'17',
          opcionpor:'',
      },
      solucion2:{
          respuestarr:'13/39',
          opcionrr:'',
          respuestadec:'0.33',
          opciondec:'',
          respuestapor:'33',
          opcionpor:'',
      },
      solucion3:{
          respuestarr:'10/39',
          opcionrr:'',
          respuestadec:'0.25',
          opciondec:'',
          respuestapor:'25',
          opcionpor:'',
      },
      solucion4:{
          respuestarr:'3/39',
          opcionrr:'',
          respuestadec:'0.07',
          opciondec:'',
          respuestapor:'7',
          opcionpor:'',
      },
      solucion5:{
          respuestarr:'1',
          opcionrr:'',
          respuestadec:'1.0',
          opciondec:'',
          respuestapor:'100',
          opcionpor:'',
      },

    }
  },
  methods:{
    comenzar(){
      this.inicio=true
    },
    verificar(opcion, respuesta){
        if(opcion==respuesta){
          this.puntos++
        }
    },
    showModal() {
        this.$refs['my-modal'].show()
        let sonido=''
      if(this.puntos>=0 && this.puntos<=5){
        sonido='/perdedor.mp3'
      }else{
         sonido='/ganador.mp3'
      }
      this.playSound(sonido)
    },
    hideModal() {
          this.$refs['my-modal'].hide()
          this.puntos=0
          this.solucion0.opcionfa='';
          this.solucion0.opcionfac='';
          this.solucion0.opcionrr='';
          this.solucion0.opciondec='';
          this.solucion0.opcionpor='';

          this.solucion1.opcionfa='';
          this.solucion1.opcionfac='';
          this.solucion1.opcionrr='';
          this.solucion1.opciondec='';
          this.solucion1.opcionpor='';

          this.solucion2.opcionfa='';
          this.solucion2.opcionfac='';
          this.solucion2.opcionrr='';
          this.solucion2.opciondec='';
          this.solucion2.opcionpor='';

          this.solucion3.opcionfa='';
          this.solucion3.opcionfac='';
          this.solucion3.opcionrr='';
          this.solucion3.opciondec='';
          this.solucion3.opcionpor='';

          this.solucion4.opcionfa='';
          this.solucion4.opcionfac='';
          this.solucion4.opcionrr='';
          this.solucion4.opciondec='';
          this.solucion4.opcionpor='';

          this.solucion5.opcionfa='';
          this.solucion5.opcionfac='';
          this.solucion5.opcionrr='';
          this.solucion5.opciondec='';
          this.solucion5.opcionpor='';

    },
    playSound (sound) {
      if(sound) {
        var audio = new Audio(sound);
        audio.play();
      }
    },
  }

}
</script>
