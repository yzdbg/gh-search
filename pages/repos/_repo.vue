<template>

    <v-container>
        <h1>
          {{repo.full_name}}
        </h1>

        <FileCard v-for="file in contents"
        :key="file.sha"
        :file="file"
        />
        <v-container id="readme">
          
        </v-container>
    </v-container>

</template>

<script>
import marked from 'marked'
export default {
 
  data() {
    return {};
  },
  async asyncData({ params, $axios }) {
      const username = params.repo.split("-")[0]
      const reponame = params.repo.split("-").slice(1).join("-")
    const [repoRes, contentsRes, readmeRes] = await Promise.all([
      $axios.$get(`https://api.github.com/repos/${username}/${reponame}`),
      $axios.$get(`https://api.github.com/repos/${username}/${reponame}/contents/`),
      $axios.$get(`https://raw.githubusercontent.com/${username}/${reponame}/master/README.md`)
    ]);
    console.log(readmeRes);
    console.log(marked(readmeRes));

    return {
      repo: repoRes,
      contents: contentsRes,
      readme: readmeRes
    };
  },
  methods: {
    parseMarkdown(){
      document.getElementById('readme').innerHTML +=marked(this.readme)
    }
  },
  mounted(){
    this.parseMarkdown()
  }
};
</script>

<style lang="scss" scoped>

</style>