<template>
  <v-app>
    <home-tool-bar />
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import HomeToolBar from './views/HomeToolBar.vue'  

export default {
  name: 'App',
  components: {
      HomeToolBar,
    },
  data: () => ({
    //
  }),
};
</script>
