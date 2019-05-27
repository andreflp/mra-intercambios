<template>
  <v-layout justify-center>
    <v-flex xs7 mg-top>
      <DTable title="Orçamentos"/>
    </v-flex>
  </v-layout>
</template>

<script>
import DTable from "./components/DTable"
export default {
  name: "Orcamentos",

  components: {
    DTable
  },

  data: () => ({})
}
</script>

<style>
</style>
