<template>
  <div class="team">
    <h1 class="subheading grey--text">Team</h1>

    <v-container class="my-5">
      <v-layout row wrap>

        <v-flex xs12 sm6 md4 lg3 v-for="person in team" :key="person.name">
          <v-card flat class="text-xs-center ma-3">

            <v-responsive class="pt-4">
              <v-avatar size="100">
                <img :src="person.avatar">
              </v-avatar>
            </v-responsive>

            <v-card-text>
              <div class="subheading">{{ person.name }}</div>
              <div class="grey--text">{{ person.role }}</div>
            </v-card-text>

            <v-card-actions>
              <v-btn small flat color="grey">
                <v-icon small left>chat</v-icon>
                <span>Message</span>
              </v-btn>
            </v-card-actions>

          </v-card>
        </v-flex>

      </v-layout>
    </v-container>

  </div>
</template>

<script>

export default {
  data() {
    return {
      team: [
        {name: 'Rey', role: 'Web developer', avatar: '/rey-avatar.jpeg'},
        {name: 'Kylo', role: 'Graphic designer', avatar: '/kylo-avatar.jpg'},
        {name: 'Luke', role: 'Web developer', avatar: '/luke-avatar.jpg'},
        {name: 'Finn', role: 'Social media maverick', avatar: '/finn-avatar.jpg'},
        {name: 'Poe', role: 'Sales guru', avatar: '/poe-avatar.jpg'},
      ]
    }
  }
}
</script>
