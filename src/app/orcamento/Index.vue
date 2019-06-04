<template>
  <v-layout wrap mg-top>
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
        v-model="form.tipo"
        :error-messages="errors.collect('tipo de intêrcambio')"
        label="Tipo de Intercâmbio"
        data-vv-name="tipo de intercâmbio"
        :items="tipos"
        item-text="title"
        item-value="id"
        required
      ></v-autocomplete>
    </v-flex>
    <v-flex offset-xs4 xs4>
      <v-text-field
        v-model="form.periodo"
        :error-messages="errors.collect('período')"
        label="Período"
        data-vv-name="período"
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
      <v-btn color="#CD5350" dark>Enviar</v-btn>
      <v-btn color="#CD5350" dark>Limpar</v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  name: "Orcamento",

  $_veeValidate: {
    validator: "new"
  },

  data: () => ({
    form: {
      pais: "",
      tipo: "",
      periodo: "",
      obs: ""
    },

    paises: [
      { title: "Espanha", id: 2 },
      { title: "Estados Unidos", id: 3 },
      { title: "Inglaterra", id: 4 },
      { title: "Irlanda", id: 5 },
      { title: "Japão", id: 6 }
    ],
    tipos: [
      { title: "Estudos", id: 1 },
      { title: "Negócios", id: 2 },
      { title: "Trabalho", id: 3 }
    ]
  })
}
</script>

<style>
</style>
