<template>
  <v-content class="body">
    <!-- <Menu/> -->
    <Toolbar/>
    <transition name="router-anim">
      <router-view/>
    </transition>
  </v-content>
</template>

<script>
import Menu from "@/app/default/components/Menu"
import Toolbar from "@/app/default/components/Toolbar"
export default {
  name: "Default",
  components: {
    Menu,
    Toolbar
  }
}
</script>

<style>
.body {
  padding: 20px;
}
</style>
