<template>
  <div>
    <b-container fluid>
      <Navbar></Navbar>
      <b-row>
        <b-col>
          <b-jumbotron header="Sesión 1" lead="Momento 2">
            <center>
              <iframe
                width="460"
                height="315"
                src="https://www.youtube.com/embed/xOjQ3u7jSLQ"
                title="YouTube video player"
                frameborder="0"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                allowfullscreen
              >
              </iframe>
            </center>
          </b-jumbotron>
        </b-col>
      </b-row>
      <b-row>
        <b-col>
          <b-form>
            <b-label>Reponder Segun el Video</b-label>
            <b-form-textarea
              id="textarea"
              v-model="observacion"
              placeholder=""
              rows="3"
              max-rows="6"
            ></b-form-textarea> </b-form
          ><br />
          <b-button variant="success" @click="comenzar">Responder</b-button>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      observacion:''
    };
  },
};
</script>
