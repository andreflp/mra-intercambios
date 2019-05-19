<template>
  <v-layout wrap style="margin-top: 40px;">
    <v-flex offset-xs4 xs4>
      <h2>Faça seu orçamento:</h2>
      <v-autocomplete
        v-model="form.pais"
        :error-messages="errors.collect('país')"
        label="País"
        data-vv-name="país"
        required
      ></v-autocomplete>
    </v-flex>
    <v-flex offset-xs4 xs4>
      <v-text-field
        v-model="form.interesse"
        :error-messages="errors.collect('interesse')"
        label="Interesse"
        data-vv-name="interesse"
        required
      ></v-text-field>
    </v-flex>
    <v-flex offset-xs4 xs4>
      <v-textarea
        v-model="form.obs"
        :error-messages="errors.collect('observação')"
        label="Observação"
        data-vv-name="observação"
        required
      ></v-textarea>
    </v-flex>
    <v-flex offset-xs4 xs4>
      <v-btn color="primary" @click="submit">Enviar</v-btn>
      <v-btn color="primary" @click="clear">Limpar</v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  name: "Orcamentos",

  $_veeValidate: {
    validator: "new"
  },

  data: () => ({
    form: {
      pais: "",
      interesse: "",
      obs: ""
    }
  })
}
</script>

<style>
</style>
