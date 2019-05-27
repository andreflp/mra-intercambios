<template>
  <v-app id="app">
    <router-view/>
  </v-app>
</template>


<style>
.router-anim-enter-active {
  animation: coming 0.7s;
  animation-delay: 0.1s;
  opacity: 0;
}

.mg-top {
  margin-top: 80px;
}

@media only screen and (min-width: 2560px) {
  .main-container {
    padding: 0px 270px 100px 270px;
  }
}

@media only screen and (max-width: 1920px) {
  .main-container {
    padding: 0px 280px 100px 280px;
  }
}

@media only screen and (max-width: 1440px) {
  .main-container {
    padding: 0px 140px 100px 140px;
  }
}

@media only screen and (max-width: 1024px) {
  .main-container {
    padding: 0px 110px 100px 110px;
  }
}

@media only screen and (max-width: 768px) {
  .main-container {
    padding: 0px 80px 100px 80px;
  }
}

@keyframes coming {
  from {
    transform: translateX(-50px);
    opacity: 0;
  }
  to {
    transform: translateX(0px);
    opacity: 1;
  }
}
</style>

