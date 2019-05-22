<template>
  <div>
    <Toolbar/>
    <v-layout wrap main-container style="margin-top: 80px;" v-if="!logado">
      <v-flex xs5 input-space>
        <h1>Login</h1>
        <SignIn/>
      </v-flex>
      <v-flex offset-xs1 divider-align>
        <v-divider vertical style></v-divider>
      </v-flex>
      <v-flex xs5 input-space>
        <h1>Cadastre-se</h1>
        <SignUp/>
      </v-flex>
    </v-layout>
    <Perfil main-container style="margin-top: 180px;" v-else/>
  </div>
</template>

<script>
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
    Perfil
  },

  data: () => ({
    logado: false
  }),

  mounted() {
    var logado = localStorage.getItem("logado")
    if (logado != null) {
      this.logado = true
    } else {
      this.logado = false
    }
  },

  created() {
    this.$root.$on("logado", this.getLogado)
  },

  methods: {
    getLogado(logado) {
      this.logado = logado
    }
  }
}
</script>

<style>
.input-space {
  margin-top: 120px;
  padding: 0px 0px 0px 0px;
}

.main-container {
  padding: 0px 270px 100px 270px;
}

.divider-align {
  margin-top: 120px;
  height: 600px;
}
</style>
