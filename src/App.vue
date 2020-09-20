<template>
  <v-app>
    <Header-Component />
    <v-main>
      <Router-View />
    </v-main>
  </v-app>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import HeaderComponent from "@/components/Header-Component";

export default {
  name: "App",

  components: {
    HeaderComponent,
  },

  data: () => ({
    //
  }),
};
</script>
