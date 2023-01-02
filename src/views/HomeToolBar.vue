<template>
  <nav>
    <v-toolbar
      app
      dark
      dense
      src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"
    >
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Vuetify</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-export</v-icon>
      </v-btn>
    </v-toolbar>
    
    <v-navigation-drawer app v-model="drawer" class="indigo">
			<v-list>
        <v-list-item v-for="link in links" :key="link.text" router :to="link.route" @click="drawer = !drawer">
          <v-list-item-action>
            <v-icon class="white--text">{{ link.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="white--text">{{ link.text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
	</v-navigation-drawer>
  </nav>
</template>

<script>

export default {
  data: () => ({
    drawer: false,
	links: [
      { icon: 'home', text: 'Home', route: '/'},
      { icon: 'contacts', text: 'About', route: '/about'},
    ]
  }),
};
</script>