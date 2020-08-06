<template>
  <v-app>
    <Topbar/>

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
  import Topbar from '@/components/Topbar.vue'
  export default {
    name: 'App',

    components: {
      Topbar
    },

    data: () => ({
      //
    }),
    
  };
</script>