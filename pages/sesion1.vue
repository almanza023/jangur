<template>
  <div>
    <b-container fluid>
     <Navbar></Navbar>
       <br>  <br>
        <b-jumbotron header="Sesión 1" lead="Momento 1" v-show="!inicio">
          <center>
            <b-img  src="/se1.png" width="210" height="200" alt="Circle image"></b-img>
            <b-img  src="/adolescentes.png" width="210" height="200" alt="Circle image"></b-img>
          </center>
          <p>Encontraras una actividad donde relacionaras el termino matemático con su definición.</p>
          <p>Palabras Claves</p>
          <p>Matemáticas
              estadistica palabras
              numeros reales2
              distribucion de frecuencia
              algebra</p>

          <b-button variant="primary" @click="comenzar">Comenzar</b-button>
        </b-jumbotron>
        <b-flex v-show="inicio">
           <h2 >Relaciona el termino matemático con su definición.</h2>
        </b-flex>
    <b-row class="m-10" v-show="inicio">
      <b-col cols="6">
        <b-list-group>
          <b-list-group-item v-for="item in preguntas" :key="item.posicion">{{ item.respuesta }} -{{ item.descripcion }}
            <b-input
            @change="verificar(item.opcion, item.respuesta)"
            v-model="item.opcion"
            ></b-input>
            </b-list-group-item>
          </b-list-group>
      </b-col>
       <b-col cols="6">
        <b-list-group>
          <b-list-group-item  v-for="(item, index) in respuestas" :key="item.posicion">
            <b-badge variant="info">{{ index +1 }}</b-badge> {{ item.descripcion }}
            </b-list-group-item>
            <b-list-group-item>
              <center><b-img  src="/sesion1.png" width="210" height="200" rounded="circle" alt="Circle image"></b-img></center>
            </b-list-group-item>
          </b-list-group>
      </b-col>
      <br><br>


             <b-button block variant="success" @click="resultado">Resultados</b-button>


    </b-row>

      <b-modal ref="my-modal" hide-footer title="Puntaje">
      <div class="d-block text-center">
        <h2>Resultado</h2>
        <h3>Puntos Obtenidos {{ puntos }}</h3>
          <b-img v-if="(puntos>0 && puntos<=5 )" width="80" height="80" src="/bronce.gif" rounded="circle" alt="Circle image"></b-img>
          <b-img v-if="(puntos>=6 && puntos<=9 )" width="80" height="80" src="/plata.gif" rounded="circle" alt="Circle image"></b-img>
          <b-img v-if="puntos==10" src="/oro.gif" width="80" height="80" rounded="circle" alt="Circle image"></b-img>
      </div>
      <b-button class="mt-3" variant="outline-danger" block v-show="puntos<=9" @click="nuevo">Nuevo Intento</b-button>
      <b-button class="mt-3" variant="outline-primary" v-show="puntos==10" block @click="siguiente">Siguiente Sesión</b-button>
    </b-modal>

    </b-container>
  </div>


</template>
<script>
export default {
  data() {
  return {
    puntos:0,
    mostrar:false,
    inicio:false,
     preguntas:[
      {
        posicion:1,
        descripcion:'Número Racionales',
        respuesta:'9',
        opcion:''
      },
      {
        posicion:2,
        descripcion:'Población',
        respuesta:'7',
        opcion:''
      },
      {
        posicion:3,
        descripcion:'Frecuencia relativa.',
        respuesta:'3',
        opcion:''
      },
      {
        posicion:4,
        descripcion:'Números enteros.',
        respuesta:'5',
        opcion:''
      },
      {
        posicion:5,
        descripcion:'Números irracionales.',
        respuesta:'10',
        opcion:''
      },
      {
        posicion:6,
        descripcion:'Frecuencia absoluta.',
        respuesta:'2',
        opcion:''
      },
      {
        posicion:7,
        descripcion:'Dato cuantitativo.',
        respuesta:'1',
        opcion:''
      },
      {
        posicion:8,
        descripcion:'Variable',
        respuesta:'8',
        opcion:''
      },
      {
        posicion:9,
        descripcion:'Dato cualitativo.',
        respuesta:'4',
        opcion:''
      },
      {
        posicion:10,
        descripcion:'Muestra.',
        respuesta:'6',
        opcion:''
      }
     ],
     respuestas:[
      {
        posicion:1,
        descripcion:'Son valores que se obtienen mediante mediciones o conteo, por tanto, son valores numéricos asignados a cada elemento de la población o muestra.'
    },
    {
      posicion:2,
      descripcion:'Es el numero de veces que se repite cada valor de la variable.'
    },
     {
      descripcion:'Es el cociente entre la frecuencia absoluta y el numero total de datos.',
      posicion:3,
    }, {
      posicion:4,
      descripcion:'Son valores asignados a cada elemento de la población mediante un atributo.'
    },
    {
      posicion:5,
      descripcion:'Son todos los números naturales e incluyen el cero (0) y todos los números negativos.'
    },
    {
      posicion:6,
      descripcion: 'Es un subconjunto de la población.'
    },
    {
      posicion:7,
      descripcion:'Es un conjunto de medidas o el recuento de todos los elementos que presentan una característica común.'
    },
    {
      posicion:8,
      descripcion:'Es un símbolo que representa, indistintamente a uno cualquiera de los elementos de un conjunto de datos.'
    },
    {
      posicion:9,
      descripcion:'Son las fracciones que pueden formarse a partir de los números enteros y naturales. Entendemos las fracciones como cocientes de números enteros.'
    },
    {
      posicion:10,
      descripcion:'Son números decimales que no pueden expresarse ni de manera exacta ni de manera periódica.'
    }
    ]
  }
  },
  methods:{
    verificar(opcion, respuesta){
        if(opcion==respuesta){
          this.puntos++
        }else{
          this.puntos--;
          if(this.puntos<0){
            this.puntos=0
          }
        }
    },
    resultado(){
      this.$refs['my-modal'].show()
      let sonido=''
      if(this.puntos>=0 && this.puntos<=5){
        sonido='/perdedor.mp3'
      }else{
         sonido='/ganador.mp3'
      }
      this.playSound(sonido)
    },
    siguiente(){
       window.$nuxt.$router.push('/sesion1m2')
    },
    nuevo(){
      this.puntos=0
      this.$refs['my-modal'].hide()
        this.preguntas.forEach(function(element) {
          element.opcion='';
      })
    },
    playSound (sound) {
      if(sound) {
        var audio = new Audio(sound);
        audio.play();
      }
    },
    comenzar(){
      this.inicio=true
    }
  }
}
</script>
