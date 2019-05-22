<template>
  <v-layout wrap>
    <v-flex offset-xs4 xs4>
      <h2 style="margin-bottom: 10px;">Meu Perfil</h2>
      <v-text-field
        label="Nome"
        v-model="usuario.nome"
        v-validate="'required'"
        :error-messages="errors.collect('nome')"
        data-vv-name="nome"
        required
      />
    </v-flex>
    <v-flex offset-xs4 xs4>
      <v-text-field
        label="Sobrenome"
        v-model="usuario.sobrenome"
        v-validate="'required'"
        :error-messages="errors.collect('sobrenome')"
        data-vv-name="sobrenome"
        required
      />
    </v-flex>
    <v-flex offset-xs4 xs4>
      <v-text-field
        label="CPF"
        v-model="usuario.cpf"
        v-validate="'required'"
        :error-messages="errors.collect('cpf')"
        :mask="masks.cpf"
        data-vv-name="cpf"
        required
      />
    </v-flex>
    <v-flex offset-xs4 xs4>
      <v-text-field
        label="E-mail"
        v-model="usuario.email"
        v-validate="'required|email'"
        :error-messages="errors.collect('email')"
        data-vv-name="email"
        required
      />
    </v-flex>
    <v-flex offset-xs4 xs4>
      <v-text-field
        label="Data de Nascimento"
        v-model="usuario.dataNasc"
        v-validate="'required'"
        :error-messages="errors.collect('data de nascimento')"
        :mask="masks.date"
        data-vv-name="data de nascimento"
        required
      />
    </v-flex>
    <v-flex offset-xs4 xs4>
      <v-text-field
        label="Telefone"
        v-model="usuario.telefone"
        v-validate="'required'"
        :mask="masks.telefone"
        :error-messages="errors.collect('telefone')"
        data-vv-name="telefone"
        required
      />
    </v-flex>
    <v-flex offset-xs4 xs8>
      <v-btn color="primary" @click="submit">Editar</v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
import masks from "@/utils/masks"
export default {
  $_veeValidate: {
    validator: "new"
  },

  data: () => ({
    usuario: {},
    masks,
    show: false
  }),

  mounted() {
    this.usuario = JSON.parse(localStorage.getItem("logado"))
  },

  methods: {
    submit() {
      this.$validator.validateAll().then(valid => {
        if (valid) {
          localStorage.setItem(
            `${this.usuario.email}`,
            JSON.stringify(this.usuario)
          )
          this.clear()
        }
      })
    },

    clear() {
      this.usuario.nome = ""
      this.usuario.sobrenome = ""
      this.usuario.cpf = ""
      this.usuario.email = ""
      this.usuario.emailConfirm = ""
      this.usuario.dataNasc = ""
      this.usuario.telefone = ""
      this.usuario.senha = ""
      this.$validator.reset()
    }
  }
}
</script>

<style>
</style>
