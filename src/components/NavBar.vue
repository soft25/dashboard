<template>
<nav>
    <v-toolbar flat app>
        <v-toolbar-side-icon color="grey--text"  @click="drawer = !drawer"></v-toolbar-side-icon>
        <v-toolbar-title class="text-uppercase grey--text">
            <span class="font-weight-light headline">admin</span>
            <span class="display-1">ownest</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items dark class="hidden-sm-and-down">
            <v-btn flat color="grey">
            <span>Sign out</span> 
            <v-icon right="">exit_to_app</v-icon>
            </v-btn>
        </v-toolbar-items>
    </v-toolbar>

    <v-navigation-drawer app v-model="drawer" class="light-blue darken-3">
        <v-list>
            <v-list-tile
                v-for="item in items"
                :key="item.title"
                route
                :to="item.route"
                @click=""
            >
                <v-list-tile-action>
                <v-icon class="grey--text">{{ item.icon }}</v-icon>
                </v-list-tile-action>

                <v-list-tile-content>
                <v-list-tile-title class="grey--text">{{ item.title }}</v-list-tile-title>
                </v-list-tile-content>
            </v-list-tile>
        </v-list>
    </v-navigation-drawer>
</nav>
    
</template>

<script>
export default {
    data () {
      return {
        drawer: false,
        items: [
          { title: 'Dashboard', icon: 'dashboard', route: '/' },
          { title: 'My projects', icon: 'folder', route: '/projects' },
          { title: 'Team', icon: 'person', route: '/team' }
        ]
      }
    }
}
</script>