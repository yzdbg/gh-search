<template>
  <v-card color="grey darken-3" dark>
    <v-container>
      <v-container class="pa-0 ma-0 d-flex justify-space-between align-start">
        <v-container>
          <v-row
          align="center">
            <v-col sm="8">
              <v-card-title class="px-0 text-h5">{{ repo.name }}</v-card-title>
            </v-col>
            <v-col
            sm="2"
            class="pa-0 ma-0">
              <svg aria-label="stars" role="img" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-star">
               <path fill="white" d="M8 .25a.75.75 0 01.673.418l1.882 3.815 4.21.612a.75.75 0 01.416 1.279l-3.046 2.97.719 4.192a.75.75 0 01-1.088.791L8 12.347l-3.766 1.98a.75.75 0 01-1.088-.79l.72-4.194L.818 6.374a.75.75 0 01.416-1.28l4.21-.611L7.327.668A.75.75 0 018 .25zm0 2.445L6.615 5.5a.75.75 0 01-.564.41l-3.097.45 2.24 2.184a.75.75 0 01.216.664l-.528 3.084 2.769-1.456a.75.75 0 01.698 0l2.77 1.456-.53-3.084a.75.75 0 01.216-.664l2.24-2.183-3.096-.45a.75.75 0 01-.564-.41L8 2.694v.001z"></path>
              </svg>
              {{repo.stargazers_count}}
            </v-col>
            <v-col
            sm="2"
            class="pa-0 ma-0">
              <svg aria-label="forks" role="img" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-repo-forked">
                  <path fill="white" d="M5 3.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm0 2.122a2.25 2.25 0 10-1.5 0v.878A2.25 2.25 0 005.75 8.5h1.5v2.128a2.251 2.251 0 101.5 0V8.5h1.5a2.25 2.25 0 002.25-2.25v-.878a2.25 2.25 0 10-1.5 0v.878a.75.75 0 01-.75.75h-4.5A.75.75 0 015 6.25v-.878zm3.75 7.378a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm3-8.75a.75.75 0 100-1.5.75.75 0 000 1.5z"></path>
              </svg>
              {{repo.forks_count}}
            </v-col>

          </v-row>

          <v-card-subtitle class="px-0">{{ repo.description }}</v-card-subtitle>
        </v-container>
      </v-container>

      <v-card-actions>
        <NuxtLink :to="`/repos/${user}-${repo.name}`"><v-btn text> More Info </v-btn></NuxtLink>
      </v-card-actions>
    </v-container>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
    };
  },
  
  props: ["repo","user"],

};
</script>

<style scoped>
</style>