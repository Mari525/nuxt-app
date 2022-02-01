<template>
	<v-container fluid>
      <v-app-bar
      color="deep-purple"
      class="d-flex"
      >	
        <v-img :src="require('~/static/vuetify-logo.svg')" height="40" width="40" />

        <v-btn class="ml-9" outlined>
          <nuxt-link to="/" class="white--text">Главная</nuxt-link>
        </v-btn>
        <v-btn class="ml-9" outlined>
          <nuxt-link to="/news" class="white--text">Новости</nuxt-link>
        </v-btn>
        <v-btn class="ml-9 mr-16" outlined>
          <nuxt-link to="/galler" class="white--text">Галерея</nuxt-link>
        </v-btn>

        <v-text-field
          label="Поиск"
          :rules="rules"
          hide-details="auto"
		  class="white--text"
        ></v-text-field>
        <v-icon>mdi-search-web</v-icon>
      </v-app-bar>
    </v-container>
</template>

<script>
export default {

}
</script>
