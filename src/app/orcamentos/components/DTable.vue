<template>
  <v-card>
    <v-card-title>
      <h2>{{ title }}</h2>
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="search"
        label="Pesquisar"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table :headers="headers" :items="orcamentos" :search="search">
      <template v-slot:items="props">
        <td class="text-xs-left">{{ props.item.pais }}</td>
        <td class="text-xs-left">{{ props.item.tipo }}</td>
        <td class="text-xs-left">{{ props.item.periodo }}</td>
        <td class="text-xs-left">{{ props.item.preco }}</td>
        <td class="text-xs-left">{{ props.item.situacao }}</td>
      </template>
    </v-data-table>
  </v-card>
</template>

<script>
export default {
  props: {
    title: String
  },
  data() {
    return {
      search: "",
      headers: [
        {
          text: "País",
          align: "left",
          sortable: false,
          value: "pais"
        },
        { text: "Tipo Intercâmbio", value: "tipo" },
        { text: "Período", value: "periodo" },
        { text: "Preço", value: "preco" },
        { text: "Situação", value: "situacao" }
      ],
      orcamentos: [
        {
          pais: "Estados Unidos",
          tipo: "Trabalho",
          periodo: "6 Mêses",
          preco: "R$ 6.999,90",
          situacao: "Finalizado"
        },
        {
          pais: "Inglaterra",
          tipo: "Estudos",
          periodo: "5 Mêses",
          preco: "R$ 7.500,00",
          situacao: "Finalizado"
        },
        {
          pais: "Irlanda",
          tipo: "Negócios",
          periodo: "6 Mêses",
          preco: "-",
          situacao: "Pendente"
        }
      ]
    }
  }
}
</script>

<style>
</style>
