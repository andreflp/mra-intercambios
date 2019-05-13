<template>
  <v-toolbar :clipped-left="$vuetify.breakpoint.lgAndUp" color="blue darken-3" dark app fixed>
    <v-toolbar-title style="width: 300px" class="ml-0 pl-3">
      <span class="hidden-sm-and-down">MRA</span>
    </v-toolbar-title>
    <v-text-field
      flat
      solo-inverted
      hide-details
      prepend-inner-icon="search"
      label="Pesquisar"
      class="hidden-sm-and-down"
    />
    <v-spacer></v-spacer>
    <span style="font-size: 17px">Olá, User</span>
    <v-btn icon>
      <v-icon style="font-size: 30px;">account_circle</v-icon>
    </v-btn>
  </v-toolbar>
</template>

<script>
export default {
  data: () => ({
    dialog: false,
    drawer: null,
    items: [
      { icon: "contacts", text: "Pacotes" },
      { icon: "history", text: "Cursos" },
      { icon: "content_copy", text: "Duplicates" },
      {
        icon: "keyboard_arrow_up",
        "icon-alt": "keyboard_arrow_down",
        text: "Labels",
        model: true,
        children: [{ icon: "add", text: "Create label" }]
      },
      {
        icon: "keyboard_arrow_up",
        "icon-alt": "keyboard_arrow_down",
        text: "More",
        model: false,
        children: [
          { text: "Import" },
          { text: "Export" },
          { text: "Print" },
          { text: "Undo changes" },
          { text: "Other contacts" }
        ]
      },
      { icon: "settings", text: "Settings" }
    ]
  })
}
</script>
