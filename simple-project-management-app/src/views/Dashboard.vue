<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>

    <v-container class="my-5">
      <!-- good practice is to start with smallest screen size first -->

      <v-layout row class="mb-3">

        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('title')" slot="activator">
            <v-icon left small>folder</v-icon>
            <span class="caption text-lowercase">By project title</span>
          </v-btn>
          <span>Sort by project</span>
        </v-tooltip>

        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('person')" slot="activator">
            <v-icon left small>person</v-icon>
            <span class="caption text-lowercase">By person</span>
          </v-btn>
          <span>Sort by person</span>
        </v-tooltip>

      </v-layout>

      <v-card flat v-for="project in projects" :key="project.title">

        <v-layout row wrap :class="`pa-3 project ${kebabCase(project.status)}`">
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
              <v-chip small :class="`${kebabCase(project.status)} white--text caption my-2`">{{ project.status }}</v-chip>
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
  data(){
    return {
      projects: [
        {title: 'Design a new website', person: 'Rey', due: '1st Jun 2019', status: 'In progress', content: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsa accusamus, perferendis nihil sunt ipsum earum suscipit, sit delectus, possimus deleniti laboriosam dignissimos quos officia incidunt reiciendis nulla molestiae. Nesciunt, velit.'},
        {title: 'Code up the homepage', person: 'Finn', due: '10th Jun 2019', status: 'Completed', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sequi nihil reprehenderit porro excepturi rerum magni pariatur officia? Nobis pariatur explicabo molestiae, sunt unde nihil, porro minima, odio ad neque perferendis?'},
        {title: 'Design video thumbnails', person: 'Luke', due: '20th Jun 2019', status: 'Completed', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum fuga quibusdam culpa tenetur, in adipisci officiis consectetur labore, optio rerum pariatur quas modi voluptatem possimus illo nemo? Blanditiis, vel placeat.'},
        {title: 'Create a community forum', person: 'Kylo', due: '25th Mar 2019', status: 'Overdue', content: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Optio quae tenetur pariatur, rerum ipsam omnis ad cupiditate ex soluta, quasi suscipit eum deserunt. Ducimus quo aspernatur saepe deserunt, ullam tempore.'},
      ]
    }
  },
  methods: {
    kebabCase(s) {
      return s.replace(/\s+/g, '-').toLowerCase();
    },
    sortBy(prop) {
      this.projects.sort((a, b) => a[prop] < b[prop] ? -1 : 1);
    }
  }
}
</script>

<style>

.project.completed {
  border-left: 4px solid #3cd1c2
}

.project.overdue {
  border-left: 4px solid tomato
}

.project.in-progress {
  border-left: 4px solid orange
}

.v-chip.completed {
  background: #3cd1c2
}

.v-chip.overdue {
  background: #f83e70
}

.v-chip.in-progress {
  background: #ffaa2c
}

</style>
