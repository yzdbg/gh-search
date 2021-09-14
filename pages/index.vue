<template>
  <v-container>
    <UserCard
      v-for="user in items"
      :key="user.id"
      :userInfo="user"
      class="ma-5"
    />
  </v-container>
</template>


<script>
export default {
  data() {
    return {
      input: "",
      info: null,
      items: null,
    };
  },
  methods: {
    async fetchUsers() {
      const info = await this.$axios.$get(
        "https://api.github.com/search/users?q=" + this.input
      );
      this.info = info;
      this.items = info.items.slice(0, 10);
    },
    handleQuery() {
      if (this.$route.query.search) {
        this.input = this.$route.query.search;
        this.fetchUsers();
      }
    },
  },
  mounted() {
  },
  watch: {
    "$route.query": {
      handler: "handleQuery",
      immediate: true
    },
  },
  
};
</script>

<style scoped>
</style>
