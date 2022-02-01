<template>
  <v-app>
    <Header />
    <nuxt />
  </v-app>
</template>

<script>
import Header from "@/components/Header"


export default {
  name: 'DefaultLayout',
  components: { Header }
}
</script>

<style>

a {
  text-decoration: none;
}

</style>