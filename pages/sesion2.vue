<template>
  <div>
    <b-container fluid>
      <Navbar></Navbar>
       <br>  <br>
        <b-jumbotron header="Sesión 2" lead="Momento 1" v-show="!inicio">
          <center>
            <b-img  src="/se1.png" width="210" height="200" alt="Circle image"></b-img>
            <b-img  src="/adolescentes.png" width="210" height="200" alt="Circle image"></b-img>
          </center>
          <p>Tablas de Frecuencia</p>
          <b-button variant="primary" @click="comenzar">Comenzar</b-button>
        </b-jumbotron>

        <b-row v-show="inicio">
          <b-col>
            <TableSesion></TableSesion>
          </b-col>
        </b-row>
         <b-row v-show="inicio">
          <b-col>
            <div>
              <br>
            <b-label>Inserta en la tabla de distribución de frecuencia los siguientes valores  </b-label>
            <b-table-simple bordered>
              <b-tr>
                <b-th>Número de libros leídos </b-th>
                <b-th>Frecuencia absoluta </b-th>
                <b-th>Frecuencia absoluta acumulada  </b-th>
                <b-th>Representación Racional  </b-th>
                <b-th>Representación Decimal</b-th>
                <b-th>Porcentaje</b-th>
              </b-tr>
               <b-tr>
                <b-td>0</b-td>
                <b-td><b-input v-model="solucion0.opcionfa"  @change="verificar(solucion0.opcionfa, solucion0.respuestafa)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion0.opcionfac" @change="verificar(solucion0.opcionfac, solucion0.respuestafac)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion0.opcionrr"  @change="verificar(solucion0.opcionrr, solucion0.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion0.opciondec" @change="verificar(solucion0.opciondec, solucion0.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion0.opcionpor" @change="verificar(solucion0.opcionpor, solucion0.respuestapor)" type="number"></b-input></b-td>
              </b-tr>
              <b-tr>
                <b-td>1</b-td>
                <b-td><b-input v-model="solucion1.opcionfa"  @change="verificar(solucion1.opcionfa, solucion1.respuestafa)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion1.opcionfac" @change="verificar(solucion1.opcionfac, solucion1.respuestafac)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion1.opcionrr"  @change="verificar(solucion1.opcionrr, solucion1.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion1.opciondec" @change="verificar(solucion1.opciondec, solucion1.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion1.opcionpor" @change="verificar(solucion1.opcionpor, solucion1.respuestapor)" type="number"></b-input></b-td>
              </b-tr>
              <b-tr>
                <b-td>2</b-td>
                 <b-td><b-input v-model="solucion2.opcionfa" @change="verificar(solucion2.opcionfa, solucion2.respuestafa)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion2.opcionfac" @change="verificar(solucion2.opcionfac, solucion2.respuestafac)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion2.opcionrr"  @change="verificar(solucion2.opcionrr, solucion2.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion2.opciondec" @change="verificar(solucion2.opcionfa, solucion2.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion2.opcionpor" @change="verificar(solucion2.opcionfa, solucion2.respuestapor)" type="number"></b-input></b-td>
              </b-tr>
              <b-tr>
                <b-td>3</b-td>
                <b-td><b-input v-model="solucion3.opcionfa"  @change="verificar(solucion3.opcionfa, solucion3.respuestafa)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion3.opcionfac" @change="verificar(solucion3.opcionfac, solucion3.respuestafac)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion3.opcionrr"  @change="verificar(solucion3.opcionrr, solucion3.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion3.opciondec" @change="verificar(solucion3.opciondec, solucion3.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion3.opcionpor" @change="verificar(solucion3.opcionpor, solucion3.respuestapor)" type="number"></b-input></b-td>
              </b-tr>
              <b-tr>
                <b-td>4</b-td>
                <b-td><b-input v-model="solucion4.opcionfa"  @change="verificar(solucion4.opcionfa, solucion4.respuestafa)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion4.opcionfac" @change="verificar(solucion4.opcionfac, solucion4.respuestafac)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion4.opcionrr"  @change="verificar(solucion4.opcionrr, solucion4.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion4.opciondec" @change="verificar(solucion4.opciondec, solucion4.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion4.opcionpor" @change="verificar(solucion4.opcionpor, solucion4.respuestapor)" type="number"></b-input></b-td>
              </b-tr>
              <b-tr>
                <b-td>5</b-td>
                <b-td><b-input v-model="solucion5.opcionfa"  @change="verificar(solucion5.opcionfa, solucion5.respuestafa)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion5.opcionfac" @change="verificar(solucion5.opcionfac, solucion5.respuestafac)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion5.opcionrr"  @change="verificar(solucion5.opcionrr, solucion5.respuestarr)" type="text"></b-input></b-td>
                <b-td><b-input v-model="solucion5.opciondec" @change="verificar(solucion5.opciondec, solucion5.respuestadec)" type="number"></b-input></b-td>
                <b-td><b-input v-model="solucion5.opcionpor" @change="verificar(solucion5.opcionpor, solucion5.respuestapor)" type="number"></b-input></b-td>
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
          <b-img v-if="(puntos>=0 && puntos<=9 )" width="80" height="80" src="/bronce.gif" rounded="circle" alt="Circle image"></b-img>
          <b-img v-if="(puntos>=9 && puntos<=19 )" width="80" height="80" src="/plata.gif" rounded="circle" alt="Circle image"></b-img>
          <b-img v-if="puntos==20" src="/oro.gif" width="80" height="80" rounded="circle" alt="Circle image"></b-img>
      </div>
      <b-button class="mt-3" variant="outline-danger" block v-show="puntos<=19" @click="nuevo">Nuevo Intento</b-button>
      <b-button class="mt-3" variant="outline-primary" v-show="puntos==20" block @click="siguiente">Siguiente Sesión</b-button>
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
          respuestafa:'2',
          opcionfa:'',
          respuestafac:'2',
          opcionfac:'',
          respuestarr:'2/30',
          opcionrr:'',
          respuestadec:'0.07',
          opciondec:'',
          respuestapor:'7',
          opcionpor:'',
      },
      solucion1:{
          respuestafa:'7',
          opcionfa:'',
          respuestafac:'9',
          opcionfac:'',
          respuestarr:'7/30',
          opcionrr:'',
          respuestadec:'0.23',
          opciondec:'',
          respuestapor:'23',
          opcionpor:'',
      },
      solucion2:{
          respuestafa:'9',
          opcionfa:'',
          respuestafac:'18',
          opcionfac:'',
          respuestarr:'9/30',
          opcionrr:'',
          respuestadec:'0.30',
          opciondec:'',
          respuestapor:'30',
          opcionpor:'',
      },
      solucion3:{
          respuestafa:'6',
          opcionfa:'',
          respuestafac:'24',
          opcionfac:'',
          respuestarr:'6/30',
          opcionrr:'',
          respuestadec:'0.20',
          opciondec:'',
          respuestapor:'20',
          opcionpor:'',
      },
      solucion4:{
          respuestafa:'4',
          opcionfa:'',
          respuestafac:'28',
          opcionfac:'',
          respuestarr:'13/30',
          opcionrr:'',
          respuestadec:'0.13',
          opciondec:'',
          respuestapor:'13',
          opcionpor:'',
      },
      solucion5:{
          respuestafa:'2',
          opcionfa:'',
          respuestafac:'30',
          opcionfac:'',
          respuestarr:'2/30',
          opcionrr:'',
          respuestadec:'0.07',
          opciondec:'',
          respuestapor:'7',
          opcionpor:'',
      },

    }
  },
  methods:{
    siguiente(){
       window.$nuxt.$router.push('/sesion2m2')
    },
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
