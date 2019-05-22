<template>
  <form>
    <v-text-field
      label="E-mail"
      v-model="form.usuario"
      v-validate="'required|email'"
      :error-messages="errors.collect('email')"
      data-vv-name="email"
      required
    ></v-text-field>
    <v-text-field
      label="Senha"
      browser-autocomplete="new-password"
      v-model="form.senha"
      v-validate="'required'"
      :error-messages="errors.collect('senha')"
      data-vv-name="senha"
      required
      :append-icon="show ? 'visibility' : 'visibility_off'"
      :type="show ? 'text' : 'password'"
      @click:append="show = !show"
    ></v-text-field>

    <v-btn color="primary" @click="submit">Login</v-btn>
    <v-btn color="primary" @click="clear">Limpar</v-btn>
  </form>
</template>

<script>
export default {
  $_veeValidate: {
    validator: "new"
  },

  data: () => ({
    form: {
      usuario: "",
      senha: ""
    },
    show: false,
    logado: false
  }),

  methods: {
    submit() {
      this.$validator.validateAll().then(valid => {
        if (valid) {
          let usuario = JSON.parse(localStorage.getItem(`${this.form.usuario}`))
          if (usuario == null || usuario.senha != this.form.senha) {
            alert("Email ou senha incorretos")
          } else {
            this.logado = true
            this.$router.push("/login")
            this.$root.$emit("logado", this.logado)
            localStorage.setItem("logado", JSON.stringify(usuario))

            this.clear()
          }
        }
      })
    },

    clear() {
      this.form.usuario = ""
      this.form.senha = ""
      this.$validator.reset()
    }
  }
}
</script>

<style>
</style>
