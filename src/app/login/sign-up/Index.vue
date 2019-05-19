<template>
  <form>
    <v-text-field
      v-model="form.nome"
      :error-messages="errors.collect('nome')"
      label="Nome"
      data-vv-name="nome"
      required
    ></v-text-field>
    <v-text-field
      v-model="form.sobrenome"
      :error-messages="errors.collect('sobrenome')"
      label="Sobrenome"
      data-vv-name="sobrenome"
      required
    ></v-text-field>
    <v-text-field
      v-model="form.cpf"
      :error-messages="errors.collect('cpf')"
      label="CPF"
      data-vv-name="cpf"
      required
    ></v-text-field>
    <v-text-field
      v-model="form.email"
      v-validate="'required|email'"
      :error-messages="errors.collect('email')"
      label="E-mail"
      data-vv-name="email"
      required
    ></v-text-field>
    <v-text-field
      v-model="form.emailConfirm"
      :error-messages="errors.collect('name')"
      label="Confirmação de E-mail"
      data-vv-name="confirmação"
      required
    ></v-text-field>
    <v-text-field
      v-model="form.dataNasc"
      :error-messages="errors.collect('data de nascimento')"
      label="Data de Nascimento"
      data-vv-name="data de nascimento"
      required
    ></v-text-field>
    <v-text-field
      v-model="form.telefone"
      :error-messages="errors.collect('telefone')"
      label="Telefone"
      data-vv-name="telefone"
      required
    ></v-text-field>
    <v-text-field
      v-model="form.senha"
      :error-messages="errors.collect('senha')"
      label="Senha"
      data-vv-name="senha"
      :append-icon="show ? 'visibility' : 'visibility_off'"
      :type="show ? 'text' : 'password'"
      @click:append="show = !show"
      required
    ></v-text-field>

    <v-btn color="primary" @click="submit">Enviar</v-btn>
    <v-btn color="primary" @click="clear">Limpar</v-btn>
  </form>
</template>

<script>
export default {
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

    show: false
  })
}
</script>

<style>
</style>
