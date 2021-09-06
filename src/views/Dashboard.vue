<template>
  <div class="home">
    <h1>Dashboard</h1>
    <v-container class="my-5">
      <v-layout row class="mb-3">
        <v-btn small depressed color="grey--text" @click="sortBy('title')">
          <v-icon depressed color="" left small>mdi-folder</v-icon>
          <span class="caption text-lowercase">By project name</span>
        </v-btn>
        <v-btn small depressed color="grey--text" @click="sortBy('person')">
          <v-icon depressed color="" left small>mdi-account</v-icon>
          <span class="caption text-lowercase">By Person</span>
        </v-btn>
      </v-layout>

      <v-card class="pa-8" v-for="project in projects" :key="project.title">
        <v-layout row wrap :class="`pa-3 project ${project.status}`">
          <v-flex xs12 md6>
            <div class="caption grey--text">Project titel</div>
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
              <v-chip
                small
                :class="`${project.status} white--text caption my-2`"
                >{{ project.status }}
              </v-chip>
            </div>
          </v-flex>
        </v-layout>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
  data() {
    return {
      projects: [
        {
          title: "Design a new Website",
          person: "The Net Ninja",
          due: "1st Sep 2021",
          status: "Overdue",
        },
        {
          title: "Code up the Home page",
          person: "Chun LI",
          due: "10 Sep 2021",
          status: "Completed",
        },
        {
          title: "Create a community forum",
          person: "Riyo",
          due: "10 Sep 2021",
          status: "Ongoing",
        },
        {
          title: "New Website",
          person: "The Ninja",
          due: "10 Sep 2021",
          status: "Ongoing",
        },
      ],
    };
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1));
    },
  },
};
</script>
<style>
.project.Completed {
  border-left: 4px solid green;
}
.project.Ongoing {
  border-left: 4px solid orange;
}
.project.Overdue {
  border-left: 4px solid tomato;
}

.v-chip.Completed {
  background: green;
}

/* .v-chip.Ongoing {
  background: orange;
}
.v-chip.overdue {
  background-color: tomato;
}
.v-chip.Completed {
  background: green;
} */
</style>
