<template>
  <v-snackbar
    v-model="snackbar"
    :bottom="y === 'bottom'"
    :left="x === 'left'"
    :multi-line="mode === 'multi-line'"
    :right="x === 'right'"
    :timeout="timeout"
    :top="y === 'top'"
    :vertical="mode === 'vertical'"
  >
    {{ text }}
    <v-btn color="light-blue accent-4" flat @click="snackbar = false">Fechar</v-btn>
  </v-snackbar>
</template>

<script>
export default {
  data: () => ({
    snackbar: false,
    y: "top",
    x: "right",
    mode: "",
    timeout: 6000,
    text: ""
  }),

  created() {
    this.$root.$on("showSnack", this.showSnack)
    this.$root.$on("showSnackSignUp", this.showSnackSignUp)
  },

  methods: {
    showSnack(snack) {
      this.text = "Seja bem vindo!"
      this.snackbar = true
    },

    showSnackSignUp(snack) {
      this.text = "Cadastrado com sucesso!"
      this.snackbar = true
    }
  }
}
</script>

<style>
</style>
