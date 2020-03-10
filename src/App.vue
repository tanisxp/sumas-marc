<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Vuetify</span>
        <span class="font-weight-light">MATERIAL DESIGN</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/">      <span class="mr-2">Home</span> </v-btn>
      <v-btn to="/sum">   <span class="mr-2">Sum</span>   </v-btn>
      <v-btn to="/about"> <span class="mr-2">About</span> </v-btn>
    </v-app-bar>
    <v-content>
      <router-view/>     
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';


export default {
  name: 'App',
  components: {
    HelloWorld
  },
  beforeMount() {
    let expiration = new Date(date).toUTCString();
    document.cookie = "record_cookie=90;expires=" + expiration + ";"
  },
  data: () => ({   
    total:1
  }),
};
</script>
