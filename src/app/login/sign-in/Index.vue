<template>
  <form>
    <v-text-field
      v-model="form.user"
      v-validate="'required|min:10'"
      :error-messages="errors.collect('usuário')"
      label="E-mail"
      data-vv-name="email"
      required
    ></v-text-field>
    <v-text-field
      v-model="form.password"
      :error-messages="errors.collect('senha')"
      label="Senha"
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
      user: "",
      password: ""
    },
    show: false
  }),

  methods: {
    submit() {
      this.$validator.validateAll()
    },

    clear() {
      this.form.user = ""
      this.form.password = ""
      this.$validator.reset()
    }
  }
}
</script>

<style>
</style>
