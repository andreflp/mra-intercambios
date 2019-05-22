<template>
  <v-layout wrap row>
    <v-flex xs6 style="padding-right: 6px">
      <v-text-field
        label="Nome"
        v-model="form.nome"
        v-validate="'required'"
        :error-messages="errors.collect('nome')"
        data-vv-name="nome"
        required
      ></v-text-field>
    </v-flex>
    <v-flex xs6 style="padding-left: 6px">
      <v-text-field
        label="Sobrenome"
        v-model="form.sobrenome"
        v-validate="'required'"
        :error-messages="errors.collect('sobrenome')"
        data-vv-name="sobrenome"
        required
      ></v-text-field>
    </v-flex>
    <v-flex xs12>
      <v-text-field
        label="CPF"
        v-model="form.cpf"
        v-validate="'required'"
        :error-messages="errors.collect('cpf')"
        :mask="masks.cpf"
        data-vv-name="cpf"
        required
      ></v-text-field>
    </v-flex>
    <v-flex xs12>
      <v-text-field
        label="E-mail"
        v-model="form.email"
        v-validate="'required|email'"
        :error-messages="errors.collect('email')"
        data-vv-name="email"
        required
      ></v-text-field>
    </v-flex>
    <v-flex xs12>
      <v-text-field
        label="Confirmação de E-mail"
        v-model="form.emailConfirm"
        v-validate="'required|email'"
        :error-messages="errors.collect('confirmação')"
        data-vv-name="confirmação"
        required
      ></v-text-field>
    </v-flex>
    <v-flex xs12>
      <v-text-field
        label="Data de Nascimento"
        v-model="form.dataNasc"
        v-validate="'required'"
        :error-messages="errors.collect('data de nascimento')"
        :mask="masks.date"
        data-vv-name="data de nascimento"
        required
      ></v-text-field>
    </v-flex>
    <v-flex xs12>
      <v-text-field
        label="Telefone"
        v-model="form.telefone"
        v-validate="'required'"
        :mask="masks.telefone"
        :error-messages="errors.collect('telefone')"
        data-vv-name="telefone"
        required
      ></v-text-field>
    </v-flex>
    <v-flex xs12>
      <v-text-field
        label="Senha"
        v-model="form.senha"
        v-validate="'required'"
        :error-messages="errors.collect('senha')"
        browser-autocomplete="new-password"
        data-vv-name="senha"
        :append-icon="show ? 'visibility' : 'visibility_off'"
        :type="show ? 'text' : 'password'"
        @click:append="show = !show"
        required
      ></v-text-field>
    </v-flex>

    <v-btn color="primary" @click="submit">Enviar</v-btn>
    <v-btn color="primary" @click="clear">Limpar</v-btn>
  </v-layout>
</template>

<script>
import masks from "@/utils/masks"
export default {
  $_veeValidate: {
    validator: "new"
  },

  data: () => ({
    form: {
      nome: "",
      sobrenome: "",
      cpf: "",
      email: "",
      emailConfirm: "",
      dataNasc: "",
      telefone: "",
      senha: ""
    },
    masks,
    show: false
  }),

  methods: {
    submit() {
      this.$validator.validateAll().then(valid => {
        if (valid) {
          localStorage.setItem(`${this.form.email}`, JSON.stringify(this.form))
          this.clear()
        }
      })
    },

    clear() {
      this.form.nome = ""
      this.form.sobrenome = ""
      this.form.cpf = ""
      this.form.email = ""
      this.form.emailConfirm = ""
      this.form.dataNasc = ""
      this.form.telefone = ""
      this.form.senha = ""
      this.$validator.reset()
    }
  }
}
</script>

<style>
</style>
