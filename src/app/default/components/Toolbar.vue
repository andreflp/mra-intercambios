<template>
  <v-toolbar color="blue darken-3" dark tabs app fixed>
    <v-spacer></v-spacer>
    <v-layout row wrap align-center style="margin-top: 5px;">
      <v-toolbar-title style="margin-right: 20px;">MRA</v-toolbar-title>
      <v-flex class="text-xs-center">
        <v-text-field flat label="Pesquisar" prepend-inner-icon="search" solo-inverted/>
      </v-flex>
      <v-toolbar-items>
        <v-menu offset-x style="margin-left: 10px">
          <template v-slot:activator="{ on }">
            <v-btn icon v-on="on">
              <v-icon style="font-size: 30px">account_circle</v-icon>
            </v-btn>
          </template>
          <v-list>
            <div v-if="!logado">
              <v-list-tile to="/login">
                <v-list-tile-title>Login</v-list-tile-title>
              </v-list-tile>
            </div>
            <div v-else>
              <v-list-tile to="/login">
                <v-list-tile-title>Meu Perfil</v-list-tile-title>
              </v-list-tile>
              <v-list-tile @click="logout">
                <v-list-tile-title>Logout</v-list-tile-title>
              </v-list-tile>
            </div>
          </v-list>
        </v-menu>
      </v-toolbar-items>
    </v-layout>
    <v-spacer></v-spacer>

    <template v-slot:extension>
      <v-tabs centered color="transparent" slider-color="white">
        <v-tab v-for="item in itemsTab" :key="item.title" :to="item.route">{{ item.title }}</v-tab>
      </v-tabs>
    </template>
  </v-toolbar>
</template>

<script>
export default {
  data: () => ({
    dialog: false,
    drawer: null,
    items: [{ title: "Login", route: "login" }],
    itemsTab: [
      { title: "Pacotes", route: "/" },
      { title: "Orçamentos", route: "orcamentos" },
      { title: "Conta", route: "login" }
    ],
    logado: false
  }),

  mounted() {
    let logado = localStorage.getItem("logado")
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
    logout() {
      let usuarioLogado = localStorage.removeItem("logado")
      this.$router.push("/")
    },

    getLogado(logado) {
      this.logado = logado
    }
  }
}
</script>


