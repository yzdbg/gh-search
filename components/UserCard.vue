<template>
  <v-card color="grey darken-3" dark >
    <v-container>
      <v-container class="pa-0 ma-0 d-flex justify-space-between align-start">
        <v-container>
          <v-card-title class="px-0 text-h5">{{ userInfo.login }}</v-card-title>

          <v-card-subtitle class="px-0">{{ info.bio }}</v-card-subtitle>
        </v-container>
        <v-avatar class="pa-0 ma-3" size="125" tile>
          <v-img :src="userInfo.avatar_url"></v-img>
        </v-avatar>
      </v-container>

      <v-card-actions>
        <NuxtLink :to="`/users/${userInfo.login}`"><v-btn text> More Info </v-btn></NuxtLink>
      </v-card-actions>
    </v-container>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      info: {
        bio: "",
      },
    };
  },
  props: ["userInfo"],
  methods: {},
  mounted() {
    this.$axios
      .$get("https://api.github.com/users/" + this.userInfo.login)
      .then((response) => (this.info = response));
  },
};
</script>

<style scoped>
</style>