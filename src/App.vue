<template>
  <v-app>
    <v-app-bar
      app
      color="blue-grey darken-4"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Tavern Logo"
          class="img-logo shrink mr-2"
          contain
          :src="require('./assets/logo.png')"
          transition="scale-transition"
          min-width="30"
          width="30"
          @click="routeHome"
        />

        <v-toolbar-title>Will's Tavern</v-toolbar-title>

      </div>

      <v-spacer></v-spacer>

      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            text
            small
            v-bind="attrs"
            v-on="on"
          >
            Help
          </v-btn>
        </template>
        <v-list>
          <v-list-item>
            <v-list-item-title><router-link to="/about">About</router-link></v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>Guidebook</v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>Feature Request</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
    <v-footer 
      dark
      color="blue-grey darken-4"
    >
      <v-spacer></v-spacer>
      <div>&copy; {{ new Date().getFullYear() }}</div>
    </v-footer>
  </v-app>
</template>

<script>
  import router from '@/router'

  export default {
    name: 'App',

    components: {
      //
    },

    data: () => ({
      //
    }),
    methods: {
      routeHome () {
        router.push({ path: '/'}).catch(()=>{})
      }
    }
  };
</script>

<style scoped>
  .img-logo {
    cursor: pointer;
  }
</style>
