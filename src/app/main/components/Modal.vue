<template>
  <v-layout row justify-center>
    <v-dialog v-model="dialog" persistent max-width="700px">
      <template v-slot:activator="{ on }">
        <v-btn
          style="width: 100%;"
          class="text-xs-center"
          v-on="on"
          dark
          color="#CD5350"
        >Ver Detalhes</v-btn>
      </template>
      <v-card>
        <v-img class="white--text" max-height="400px" :src="image"></v-img>
        <v-card-title class="padding-bottom: 0;">
          <div>
            <div class="headline">{{ title }}</div>
            <br>
            <div>
              <span style="font-weight: bold">Informações:</span> Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.
            </div>
            <br>
            <div>
              <span style="font-weight: bold">Periodo:</span>
              {{ period }}
            </div>
            <div>
              <span style="font-weight: bold">Estadia:</span>
              {{ stay }}
            </div>
            <div>
              <span style="font-weight: bold">Preço:</span>
              {{ price }}
            </div>
            <br>
          </div>
        </v-card-title>
        <v-card-actions style="margin-top: -20px;" class="justify-center">
          <v-spacer></v-spacer>
          <v-btn color="#CD5350" dark @click="dialog = false">Fechar</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-layout>
</template>

<script>
export default {
  props: {
    title: String,
    price: [String, Number],
    image: String,
    period: String,
    stay: String
  },

  data: () => ({
    dialog: false
  })
}
</script>

<style>
</style>
