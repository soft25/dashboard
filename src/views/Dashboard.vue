<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>
  
    <v-container fluid class="my-5">
      <v-layout row class="mb-2">
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('title')" slot="activator">
            <v-icon left small>folder</v-icon>
            <span class=" text-lowercase">By project name</span>
          </v-btn>
          <span>sort projects by project name</span>
        </v-tooltip>

        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('person')" slot="activator">
            <v-icon left small>person</v-icon>
            <span class=" text-lowercase">By person</span>
          </v-btn>
          <span>sort projects by person name</span>
        </v-tooltip>
      </v-layout>

      <v-card flat v-for="project in projects" :key="project.title">
        <v-layout row wrap :class="`pa-3 project ${project.status}`">
          <v-flex xs12 md6>
            <div class="caption grey--text">Project title</div>
            <div>{{ project.title }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Person</div>
            <div>{{ project.person }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Due by</div>
            <div>{{ project.due }}</div>
          </v-flex>
          <v-flex xs2 sm4 md2>
            <div class="right">
              <v-chip :class="`${project.status} white--text caption my-2`">{{ project.status }}</v-chip>  
            </div>
          </v-flex>
        </v-layout>
        <v-divider></v-divider>
      </v-card>
    </v-container>

  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        {title: 'learn some vue.js' ,person: 'sofiane KIRATI', due: '20 April 2019', status: 'overdue'},
        {title: 'create a new website' ,person: 'sofiane KIRATI', due: '27 April 2019', status: 'done'},
        {title: 'add new features' ,person: 'sofiane KIRATI', due: '28 April 2019', status: 'pending'},
        {title: 'connect to back' ,person: 'sofiane KIRATI', due: '29 April 2019', status: 'pending'},
        {title: 'secure the website' ,person: 'sofiane KIRATI', due: '30 April 2019', status: 'pending'}
      ]
    }
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1 : 1)
    }
  }
};
</script>

<style>
.project.overdue {
  border-left: 4px solid red
}
.project.done {
  border-left: 4px solid green
}
.project.pending {
  border-left: 4px solid blue
}

.v-chip.overdue {
  background: red
}
.v-chip.done {
  background: green
}
.v-chip.pending {
  background: blue
}
</style>
