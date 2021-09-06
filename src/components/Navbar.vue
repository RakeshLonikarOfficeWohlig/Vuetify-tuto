<template>
  <div>
    <nav>
      <v-toolbar flat app>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title class="text-uppercase grey--text">
          <span class="font-weight-light">Todo</span>
          <span>Ninja</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn depressed color="white">
          <span>Sing Out</span>
          <v-icon right>mdi-export</v-icon>
        </v-btn>
      </v-toolbar>
      <v-navigation-drawer app v-model="drawer" absolute bottom temporary>
        <v-list>
          <v-list-item-group
            v-model="group"
            active-class="deep-purple--text text--accent-4"
          >
            <v-list-tile
              v-for="link in links"
              :key="link.text"
              router
              :to="link.route"
            >
              <v-list-item>
                <v-list-item-title>{{ link.text }}</v-list-item-title>
              </v-list-item>
            </v-list-tile>
          </v-list-item-group>
        </v-list>
      </v-navigation-drawer>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      links: [
        { text: "Dashboard", route: "/" },
        { text: "Project", route: "/project" },
        { text: "Team", route: "/team" },
      ],
    };
  },
};
</script>

<style></style>
