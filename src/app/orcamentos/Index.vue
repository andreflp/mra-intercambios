<template>
  <v-layout wrap style="margin-top: 80px;">
    <v-flex offset-xs4 xs4>
      <h2>Faça seu orçamento:</h2>
      <v-autocomplete
        v-model="form.pais"
        :error-messages="errors.collect('país')"
        label="País"
        data-vv-name="país"
        :items="paises"
        item-text="title"
        item-value="id"
        required
      ></v-autocomplete>
    </v-flex>
    <v-flex offset-xs4 xs4>
      <v-autocomplete
        v-model="form.interesse"
        :error-messages="errors.collect('interesse')"
        label="Interesse"
        data-vv-name="interesse"
        :items="interesses"
        item-text="title"
        item-value="id"
        required
      ></v-autocomplete>
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
    },

    paises: [
      { title: "Espanha", id: 2 },
      { title: "Estados Unidos", id: 3 },
      { title: "Inglaterra", id: 4 },
      { title: "Irlanda", id: 5 },
      { title: "Japão", id: 6 }
    ],
    interesses: [
      { title: "Estudos", id: 1 },
      { title: "Negócios", id: 2 },
      { title: "Trabalho", id: 3 }
    ]
  })
}
</script>

<style>
</style>
