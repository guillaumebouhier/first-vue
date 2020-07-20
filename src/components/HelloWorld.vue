<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app clipped>
      <v-list dense>
        <v-list-item>
          <v-list-item-action>
            <v-icon>mdi-view-dashboard</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Dashboard</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
          <v-list-item-action>
            <v-icon>mdi-settings</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Settings</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar>

    <RackDisplay :store="store"></RackDisplay>

    <v-footer app>
      <span>&copy; 2020</span>
    </v-footer>
  </v-app>
</template>

<script>
import RackDisplay from "./RackDisplay";
export default {
  components: {
    RackDisplay
  },
  props: { store: Object },

  data: () => ({
    drawer: null
  }),
  created() {
    this.$vuetify.theme.dark = true;
  },
  methods: {
    rackImage(imgUrl) {
      return require("@/assets/" + imgUrl);
    }
  }
};
</script>

<style lang="css">
.rack-container {
  display: flex;
  justify-content: center;
  padding: 10px;
  opacity: 1;
}
.disabled {
  opacity: 0.2;
}
</style>
