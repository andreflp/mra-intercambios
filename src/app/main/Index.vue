<template>
  <v-app id="inspire">
    <v-container mg-top class="main-container">
      <h2 style="margin-left: 15px">Filtrar por:</h2>
      <v-layout row wrap justify-center>
        <v-flex xs4 class="btn-space">
          <v-autocomplete :items="countries" item-value="value" item-text="name" label="País"></v-autocomplete>
        </v-flex>
        <v-flex xs4 class="btn-space">
          <v-autocomplete :items="languages" item-value="value" item-text="name" label="Línguas"></v-autocomplete>
        </v-flex>
        <v-flex xs4 class="btn-space">
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
          sm12
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
          "https://1et8030c3hf1jt1dabyqv8qo-wpengine.netdna-ssl.com/files/2013/12/bray-635x361.jpg",
        price: "R$ 4.750,00",
        period: "6 Meses",
        stay: "Inclui Estadia",
        flex: 4
      },
      {
        title: "Japão",
        src:
          "http://www.vermelho.org.br/admin/arquivos/biblioteca/japaconomia71003.jpg",
        price: "R$ 5.500,00",
        period: "4 Meses",
        stay: "Inclui Estadia",
        flex: 4
      },
      {
        title: "Inglaterra",
        src:
          "data:image/jpeg;base64,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",
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

