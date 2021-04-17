<template>
  <div id="app">
        <div class="appnavbar mb-3">
    <b-navbar toggleable="md" type="dark" variant="danger">
      <b-container>
        <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

       <b-navbar-brand href="/">
        <img src="./assets/diamond.svg" width="15%" class="d-inline-block align-top mr-1 " id="imagen" alt="Kitten">HOME
        </b-navbar-brand>

         <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav>

            </b-navbar-nav>
          </b-collapse>
      </b-container>
    </b-navbar>
  </div>
    <div class="header container casinofont">
      <b-jumbotron bg-variant="" text-variant="black" border-variant="dark">
      <template #header><img src="./assets/slot777.svg" width="10%" alt=""> {{msg1}} <img src="./assets/slot777.svg" width="10%" alt=""> </template>
      
      <template #lead>
        <h2 class="colorblack mx-auto">JUEGO DE LA SUERTE</h2>
      </template>

      <hr class="my-3">

      <p class="h4 colorblack">
        Es en un juego de azar que consiste en que al presionar el boton de jugar genera 3 numeros aleatorios
        la unica forma de ganar es que los 3 numeros generados sean 7 
      </p>
    </b-jumbotron>
    </div>
    <appbody/>
    <footer>
  <div class="container">
    <div class="row">
        <div class="col-xs-12 col-md-6 text-left">
            <h5 class="lead">CONTACTO:</h5>
            <h5 class="">
            Email: luisjosearias10@gmail.com<br>
            Programacion Computacional IV<br>
            Telefono: ####-####<br>
            </h5>
        </div>

        <div class="col-xs-12 col-md-6 text-right">
            <h6 class="lead">ENCUENTRAME EN LAS REDES</h6>
            <div class="redes-footer">
              <a href="https://www.facebook.com/" target="_blank"><img class="footerimg" src="./assets/facebookwhite.svg"></a>
              <a href="https://twitter.com/Luis78791" target="_blank"><img class="footerimg" src="./assets/twitterwhite.svg"></a>
              <a href="https://www.instagram.com/luisj.01/" target="_blank"><img class="footerimg" src="./assets/instagramwhite.svg"></a>
            </div>
        </div>
    </div>
    <div class="row"> 

        <div class="col-md-12 text-right">
            <p class="small">Luis Jose Arias Reyes @2021.<br> Todos los derechos reservados.</p>
        </div>
        
    </div>

    </div>
  </footer>
  </div>
</template>

<script>
import Appbody from './components/Appbody.vue'

export default {
  name: 'App',
  components: {
    Appbody
  },
  data(){
    return{
      msg1: '7 AFORTUNADO'
    }
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rajdhani:wght@500&display=swap");
#app {
  font-family: "Rajdhani", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
footer {
  font-family: Rajdhani, sans-serif;
	background-color:#1A1A1A;
	height: 50%;
  color: rgb(255, 255, 255);
  padding-top: 15px;
  font-size: 150%;
}

.main1 { 
  display:flex;
  margin:0 auto;
}

.footerimg{
  width: 40px;
  margin-left: 10px;
}
.casinofont{
    font-family: "Casino";
    color: #6a5acd
}
.colorblack{
  color: #1A1A1A;
}
</style>
