<template>
  <div class="Appbody container mb-4">
    <hr>
    <div class="mensajes">
      <h3 class="text-right">Intentos: {{intentos}}</h3>
    </div>
    <div class="numeros row">
      <h1 class="mx-auto num">{{ numRnd1 }}</h1>
      <h1 class="mx-auto num">{{ numRnd2 }}</h1>
      <h1 class="mx-auto num">{{ numRnd3 }}</h1>
    </div>
    <button
      :disabled="isDisabled"
      class="btn-lg btn-success mb-4"
      @click="jugar()"
    >
      {{ result }}
    </button>
    <div>
      <b-alert
        id="alertwin"
        :show="ocultarAlertWin"
        variant="success"
        @dismissed="ocultarAlertWin = 0"
        @dismiss-count-down="countDownChanged"
      >
        <img src="../assets/trophy.svg" width="8%" alt="" />
        Felicidades Ganaste!
        <img src="../assets/trophy.svg" width="8%" alt="" />
      </b-alert>

      <b-alert
        id="alertOver"
        :show="ocultarAlertOver"
        variant="danger"
        @dismissed="ocultarAlertOver = 0"
        @dismiss-count-down="ocultarfallo"
      >
        <img src="../assets/game-over.svg" width="7%" alt="" />
        Suerte la proxima!
        <img src="../assets/game-over.svg" width="7%" alt="" />
      </b-alert>
    </div>
    <hr>
<b-card
        border-variant="dark"
        class="h2"
        header="Indicaciones de la actividad"
        header-bg-variant="primary"
        header-text-variant="white"
        align="center"
      >
        <b-card-text class="h5 text-justify">
    Desarrolla en forma individual, una webapp utilizando VueJs y Boostrap Vue que tenga las siguientes partes: <br> <br>
    1.  Cabecera <br>
    2.  Cuerpo: debe permitir porder jugar el maravilloso juego del 7 afortunado!, donde al presionar un botón se deben generar 3 números aleatorios, sí los tres números resultaron ser 7 ganaste sino perdiste! <br>
    3.  Pie de página debe tener tu nombre completo y correo electrónico <br>
  </b-card-text>
      </b-card>
  </div>
</template>

<script>
export default {
  name: "Appbody",
  data() {
    return {
      numRnd1: 0,
      numRnd2: 0,
      numRnd3: 0,
      result: "Jugar",
      dismissSecs: 10,
      ocultarAlertWin: 0,
      ocultarAlertOver: 0,
      t: null,
      desactivarboton: true,
      intentos: 0
    };
  },
  computed: {
    isDisabled: function() {
      return !this.desactivarboton;
    },
  },
  methods: {
    jugar() {
      // Sumar +1 a la variable de los intentos
      this.intentos ++
      // cambiar la variable que indica si el boton esta activado o desactivado
      this.desactivarboton = false
      // Quitar cualquier alerta que este en pantalla
      this.countDownChanged();
      this.ocultarfallo();
      var self = this;
      // Cambiar texto de variable que se muestra en el boton "Jugar"
      this.result = "Jugando!";
      // funcion Intervalo que genera numeros aleatorios cada 50 ms
      this.t = setInterval(() => {
        self.numRnd1 = generarRND();
        self.numRnd2 = generarRND();
        self.numRnd3 = generarRND();
      }, 50);
      // Funcion que al pasar 3 segundos (3000 ms) detiene el intervalo que se encuentra en la propiedad "t" y llama al metodo resultado
      setTimeout(() => {
        clearInterval(this.t);
        this.resultado();
      }, 3000);
    },
    resultado() {
      // Vuelve el boton a activado y el texto a "Jugar"
      this.desactivarboton = true
      this.result = "Jugar";
      // Evalua los 3 numeros finales generados
      if (this.numRnd1 == 7 && this.numRnd2 == 7 && this.numRnd3 == 7) {
        // Muestra el alert definido para el caso que se cumpla (Haya ganado el juego)
        this.showAlertWIN();
      } else {
        // Muestra el alert en el caso que haya perdido el juego (los 3 numeros no son 7)
        this.showAlertOver();
      }
    },
    // Metodos para ocultar y mostrar alertas
    countDownChanged(ocultarAlertWin) {
      this.ocultarAlertWin = ocultarAlertWin;
    },
    showAlertWIN() {
      this.ocultarAlertWin = this.dismissSecs;
    },
    showAlertOver() {
      this.ocultarAlertOver = this.dismissSecs;
    },
    ocultarfallo(ocultarAlertOver) {
      this.ocultarAlertOver = ocultarAlertOver;
    },
  },
};
// Funcion para generar numero aleatorio
function generarRND(num) {
  num = Math.floor(Math.random() * 7) + 1;
  return num;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 @font-face { 
       font-family: "Casino";
       src: url("../assets/Casino.ttf");
   }
.Appbody {
  font-family: "Rajdhani", sans-serif;
}
#alertwin {
  font-size: 50px;
  font-style: oblique;
  font-family: "Casino";
}
#alertOver {
  font-family: "Casino";
  font-size: 50px;
}
.num{
  font-family: "Casino";
  font-size: 70px;
  
}
</style>
