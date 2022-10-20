<template>
  <div>
    <b-container fluid >
        <center>
          <br><br><br><br>
          <b-card
    title="JANGUR"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-20 mt-20"
  >

    <b-card-text>
      Bienvenido a la plataforma de contenido educativo JANGUR.
    </b-card-text>
    <b-card-text>
      <p>Selecciona un Avatar</p>
       <nuxt-img src="/avatar1.png" width="100" height="100" @click="avatar1()" />
      <nuxt-img src="/avatar2.png" width="100" height="100"  @click="avatar2()"/>
    </b-card-text>
      <p>Ingrese un nombre de usuario</p>
      <b-input v-model="data.nombre">
      </b-input><br>
    <b-button @click="empezar" variant="primary">Empezar a Jugar</b-button>
  </b-card>
        </center>
    </b-container>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return {
      data:{
        nombre:'',
        avatar:''
      }
    }
  },
  methods: {
    avatar2(){
      this.data.avatar='avata1.png'
    },
    avatar2(){
      this.data.avatar='avata2.png'
    },
    empezar(){
     window.$nuxt.$router.push('/home')
    }
  }

}
</script>
