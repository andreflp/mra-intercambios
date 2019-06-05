<template>
  <div>
    <Toolbar/>
    <v-layout wrap main-container style="margin-top: 80px;" v-if="!logado">
      <v-flex lg5 md5 sm6 xs12 input-space form-left>
        <h1>Login</h1>
        <SignIn/>
      </v-flex>
      <v-flex offset-xs1 divider-align v-if="divider">
        <v-divider vertical style></v-divider>
      </v-flex>
      <v-flex lg5 md5 sm6 xs12 input-space form-right>
        <h1>Cadastre-se</h1>
        <SignUp/>
      </v-flex>
    </v-layout>
    <Perfil main-container style="margin-top: 180px;" v-else/>
    <SnackBar/>
  </div>
</template>

<script>
import SnackBar from "@/app/main/components/SnackBar"
import SignIn from "./sign-in/Index"
import SignUp from "./sign-up/Index"
import Perfil from "@/app/perfil/Index"
import Toolbar from "@/app/default/components/Toolbar"
export default {
  name: "Login",

  components: {
    Toolbar,
    SignIn,
    SignUp,
    Perfil,
    SnackBar
  },

  data: () => ({
    logado: false,
    snackBar: false,
    divider: true
  }),

  mounted() {
    var logado = localStorage.getItem("logado")
    if (logado != null) {
      this.logado = true
    } else {
      this.logado = false
    }

    this.$nextTick(function() {
      window.addEventListener("resize", this.getWindowWidth)
      this.getWindowWidth()
    })
  },

  created() {
    this.$root.$on("logado", this.getLogado)
  },

  methods: {
    getLogado(logado) {
      this.logado = logado
    },

    getWindowWidth(event) {
      let windowWidth = screen.width
      if (windowWidth <= 768) {
        this.divider = false
      } else {
        this.divider = true
      }
    }
  },

  beforeDestroy() {
    window.removeEventListener("resize", this.getWindowWidth)
  }
}
</script>

<style>
.input-space {
  margin-top: 120px;
  padding: 0px 0px 0px 0px;
}

.divider-align {
  margin-top: 120px;
  height: 600px;
}

@media only screen and (max-width: 768px) and (min-width: 426px) {
  .form-left {
    padding-right: 18px;
  }

  .form-right {
    padding-left: 18px;
  }
}
</style>
