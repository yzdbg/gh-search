<template>
 
        <v-row>
          <v-col class="my-10" md="3" justify="center" align="center">
            <v-avatar size="125">
              <v-img :src="user.avatar_url"></v-img>
            </v-avatar>
            <h1>{{ user.name }}</h1>
            <h2>{{ user.login }}</h2>
            <p>{{ user.bio }}</p>
            <p>Followers : {{ followers.length }}</p>
            <p>Following : {{ following.length }}</p>
            <p>{{ user.location }}</p>
            <p>{{ user.company }}</p>
          </v-col>
          <v-col md="9">
            <v-container>
             <RepoCard
          v-for="r in repos"
          :key="r.id"
          :repo="r"
          :user="user.login"
          class="ma-5"
        />
            </v-container>
          </v-col>
        </v-row>

</template>

<script>
export default {
  data() {
    return {};
  },
  async asyncData({ params, $axios }) {
    const [userRes, followersRes, followingRes, reposRes] = await Promise.all([
      $axios.$get(`https://api.github.com/users/${params.username}`),
      $axios.$get(`https://api.github.com/users/${params.username}/followers`),
      $axios.$get(`https://api.github.com/users/${params.username}/following`),
      $axios.$get(`https://api.github.com/users/${params.username}/repos`),
    ]);

    return {
      user: userRes,
      followers: followersRes,
      following: followingRes,
      repos: reposRes,
    };
  },
};
</script>

