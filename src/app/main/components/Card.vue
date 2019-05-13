<template>
  <v-layout>
    <v-flex xs12>
      <v-card>
        <v-img class="white--text" height="200px" :src="image"></v-img>
        <v-card-title class="padding-bottom: 0;">
          <div>
            <span class="headline">{{ title }}</span>
            <br>
            <li>{{ period }}</li>
            <li>{{ stay }}</li>
            <h2>{{ price }}</h2>
          </div>
        </v-card-title>
        <v-card-actions style="margin-top: -20px;" class="justify-center">
          <v-btn style="width: 100%;" class="text-xs-center" color="primary">Ver Detalhes</v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
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
  }
}
</script>
