<template>
  <v-toolbar color="blue darken-3" dark tabs app fixed>
    <v-spacer></v-spacer>
    <v-layout row wrap align-center style="margin-top: 5px;">
      <v-toolbar-title style="margin-right: 20px;">MRA</v-toolbar-title>
      <v-flex class="text-xs-center">
        <v-text-field flat label="Pesquisar" prepend-inner-icon="search" solo-inverted/>
      </v-flex>
      <v-toolbar-items style="margin-left: 20px;">
        <v-btn icon>
          <v-icon>account_circle</v-icon>
        </v-btn>
      </v-toolbar-items>
    </v-layout>
    <v-spacer></v-spacer>

    <template v-slot:extension>
      <v-tabs v-model="tabs" centered color="transparent" slider-color="white">
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
    ]
  })
}
</script>


