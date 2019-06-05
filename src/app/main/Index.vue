<template>
  <v-app id="inspire">
    <v-container mg-top class="main-container">
      <h2 style="margin-left: 15px">Filtrar por:</h2>
      <v-layout row wrap>
        <v-flex lg4 md4 sm4 xs12 class="btn-space">
          <v-autocomplete :items="countries" item-value="value" item-text="name" label="País"></v-autocomplete>
        </v-flex>
        <v-flex lg4 md4 sm4 xs12 class="btn-space">
          <v-autocomplete :items="languages" item-value="value" item-text="name" label="Línguas"></v-autocomplete>
        </v-flex>
        <v-flex lg4 md4 sm4 xs12 class="btn-space">
          <v-autocomplete :items="prices" item-value="value" item-text="name" label="Preço"></v-autocomplete>
        </v-flex>
      </v-layout>
      <v-layout row wrap style="margin-top: 70px">
        <v-flex
          v-for="card in cards"
          :key="card.title"
          style="padding: 0px 10px 40px 10px"
          lg3
          md4
          sm6
          xs12
        >
          <Card
            :title="card.title"
            :image="card.src"
            :price="card.price"
            :period="card.period"
            :stay="card.stay"
          />
        </v-flex>
      </v-layout>
    </v-container>
  </v-app>
</template>

<script>
import Card from "@/app/main/components/Card"

export default {
  components: {
    Card
  },

  data: () => ({
    cards: [
      {
        title: "Estados Unidos",
        src:
          "https://travelmate.com.br/wp-content/uploads/2018/12/qual-pais-e-o-maior-entre-estados-unidos-e-india.jpg",
        price: "R$ 6.999,90",
        period: "6 Meses",
        stay: "Inclui Estadia",
        flex: 4
      },
      {
        title: "Irlanda",
        src:
          "https://www.estudarfora.org.br/app/uploads/2018/07/interc%C3%A2mbio-de-idiomas-na-Irlanda-1.jpg",
        price: "R$ 4.750,00",
        period: "6 Meses",
        stay: "Inclui Estadia",
        flex: 4
      },
      {
        title: "Japão",
        src:
          "https://i0.wp.com/seguroviagempro.com.br/wp-content/uploads/2018/12/seguro-viagem-japao.jpg?resize=780%2C405&ssl=1",
        price: "R$ 5.500,00",
        period: "4 Meses",
        stay: "Inclui Estadia",
        flex: 4
      },
      {
        title: "Inglaterra",
        src:
          "http://www.intercambiodireto.com/blog/wp-content/uploads/2018/02/Inglaterra-enjoy-intercambio-960px.jpg",
        price: "R$ 7.500,00",
        period: "5 Meses",
        stay: "Não Inclui Estadia",
        flex: 4
      },
      {
        title: "Espanha",
        src:
          "https://www.estudarfora.org.br/app/uploads/2018/05/curso-de-ver%C3%A3o-na-Espanha-1024x683.jpg",
        price: "R$ 6.999,90",
        period: "6 Meses",
        stay: "Inclui Estadia",
        flex: 4
      }
    ],
    countries: [
      { name: "Espanha", value: 2 },
      { name: "Estados Unidos", value: 3 },
      { name: "Inglaterra", value: 4 },
      { name: "Irlanda", value: 5 },
      { name: "Japão", value: 6 }
    ],
    languages: [
      { name: "Inglês", value: 4 },
      { name: "Espanhol", value: 1 },
      { name: "Alemão", value: 3 },
      { name: "Francês", value: 6 },
      { name: "Japones", value: 5 },
      { name: "Italiano", value: 2 }
    ],
    prices: [
      { name: "Maiores", value: 4 },
      { name: "Menores", value: 1 },
      { name: "Mais Populares", value: 3 }
    ]
  })
}
</script>

<style>
.btn-space {
  padding: 0px 15px 0px 15px;
}
</style>

