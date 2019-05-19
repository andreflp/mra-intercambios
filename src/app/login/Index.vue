<template>
  <v-container>
    <Toolbar/>
    <v-layout wrap main-container style="margin-top: 40px;">
      <v-flex xs5 input-space>
        <h1>Login</h1>
        <SignIn/>
      </v-flex>
      <v-flex offset-xs1 divider-align>
        <v-divider vertical style></v-divider>
      </v-flex>
      <v-flex xs5 input-space>
        <h1>Cadastre-se</h1>
        <SignUp/>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import SignIn from "./sign-in/Index"
import SignUp from "./sign-up/Index"
import Toolbar from "@/app/default/components/Toolbar"
export default {
  name: "Login",

  components: {
    Toolbar,
    SignIn,
    SignUp
  }
}
</script>

<style>
.input-space {
  margin-top: 120px;
  padding: 0px 0px 0px 0px;
}

.main-container {
  padding: 0px 270px 100px 270px;
}

.divider-align {
  margin-top: 120px;
  height: 600px;
}
</style>
