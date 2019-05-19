<template>
  <v-content class="body">
    <Toolbar/>
    <transition name="router-anim">
      <router-view/>
    </transition>
  </v-content>
</template>

<script>
import Toolbar from "@/app/default/components/Toolbar"
export default {
  name: "Default",
  components: {
    Toolbar
  }
}
</script>

<style>
.body {
  padding: 20px;
}
</style>
