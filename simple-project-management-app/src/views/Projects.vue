<template>
  <div class="projects">
    <h1 class="subheading grey--text">Projects</h1>

    <v-container class="my-5">

      <v-expansion-panel>
        <v-expansion-panel-content v-for="project in myProjects" :key="project.title">
          <!-- alignment of arrow using template tag was off -->
          <!-- <template v-slot:header>project title</template> -->
          <div slot="header">{{ project.title }}</div>
          <v-card>
            <v-card-text class="px-4 grey--text">
              <div class="font-weight-bold">Due by {{ project.due }}</div>
              <div>{{ project.content }}</div>
            </v-card-text>
          </v-card>
        </v-expansion-panel-content>
      </v-expansion-panel>

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
        {title: 'Design a new website... again', person: 'Rey', due: '1st Aug 2019', status: 'In progress', content: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsa accusamus, perferendis nihil sunt ipsum earum suscipit, sit delectus, possimus deleniti laboriosam dignissimos quos officia incidunt reiciendis nulla molestiae. Nesciunt, velit.'},
      ]
    }
  },
  computed: {
    myProjects() {
      return this.projects.filter(project => {
        return project.person === 'Rey';
      });
    }
  }
}
</script>
