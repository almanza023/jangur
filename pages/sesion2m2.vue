<template>
  <div>
    <b-container fluid>
      <Navbar></Navbar>

         <b-row >
          <b-col>
            <div>
              <br>
              <h1>Actividad 2</h1>
            <b-label>Selecciona si el enunciado es Verdadero o Falso </b-label>
            <b-table-simple bordered>
              <b-tr>
                <b-th>En la columna de frecuencia absoluta se utilizan los números Racionales  </b-th>
                 <b-td>  <b-form-select @change="verificar(solucion.opcion1, solucion.respuesta1)" v-model="solucion.opcion1"  :options="options" size="sm" class="mt-3"></b-form-select></b-td>
                </b-tr>
                <b-tr>
                <b-th>La variable utilizada en la información anterior es de tipo cualitativa </b-th>
                <b-td>  <b-form-select @change="verificar(solucion.opcion2, solucion.respuesta2)" v-model="solucion.opcion2"  :options="options" size="sm" class="mt-3"></b-form-select></b-td>
                </b-tr>
                <b-tr>
                <b-th>Los datos de la columna frecuencia acumulada se representan con numero Reales   </b-th>
                 <b-td>  <b-form-select @change="verificar(solucion.opcion3, solucion.respuesta3)" v-model="solucion.opcion3"  :options="options" size="sm" class="mt-3"></b-form-select></b-td>
                </b-tr>
                <b-tr>
                <b-th>El total de la muestra hacen parte de los números enteros  </b-th>
                 <b-td>  <b-form-select @change="verificar(solucion.opcion4, solucion.respuesta4)" v-model="solucion.opcion4"  :options="options" size="sm" class="mt-3"></b-form-select></b-td>
                </b-tr>
                <b-tr>
                <b-th>Los conjuntos numéricos utilizados son  parte de los números Reales</b-th>
                <b-td>  <b-form-select @change="verificar(solucion.opcion5, solucion.respuesta5)" v-model="solucion.opcion5"  :options="options" size="sm" class="mt-3"></b-form-select></b-td>
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
          <b-img v-if="(puntos>=1 && puntos<=2 )" width="80" height="80" src="/bronce.gif" rounded="circle" alt="Circle image"></b-img>
          <b-img v-if="(puntos>=3 && puntos<=4 )" width="80" height="80" src="/plata.gif" rounded="circle" alt="Circle image"></b-img>
          <b-img v-if="puntos==5" src="/oro.gif" width="80" height="80" rounded="circle" alt="Circle image"></b-img>
      </div>
      <b-button class="mt-3" variant="outline-danger" block v-show="puntos<=4" @click="nuevo">Nuevo Intento</b-button>
      <b-button class="mt-3" variant="outline-primary" v-show="puntos==5" block @click="siguiente">Siguiente Sesión</b-button>
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
      options: [
          { value: null, text: '' },
          { value: 'V', text: 'V' },
          { value: 'F', text: 'F' },
        ],
      solucion:{
          respuesta1:'V',
          respuesta2:'V',
          respuesta3:'V',
          respuesta4:'V',
          respuesta5:'V',
          opcion1:'',
          opcion2:'',
          opcion3:'',
          opcion4:'',
          opcion5:'',
      },

    }
  },
  methods:{
    siguiente(){
       window.$nuxt.$router.push('/sesion3')
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
            this.solucion.opcion1='';
            this.solucion.opcion2='';
            this.solucion.opcion3='';
            this.solucion.opcion4='';
            this.solucion.opcion5='';

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
