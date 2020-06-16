<template>
  <div class="container">
    <div>
      <LazyHomepageHeader :data="content.header" v-if="content.header" />
      <div class="page-bg">
      <LazyHomepageIntro :data="content.intro" v-if="content.intro" />
      <LazyHomepageFeatures :data="content.features" v-if="content.features" />
      <LazyHomepageSpecialProject :data="content.special_project" v-if="content.special_project" />
      <LazyHomepageFeaturedArticles />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, error }) {
    try {
      const content = await $axios.$get('/api/home-page')
      return { content }
    } catch(e) {
      console.log("error", e);
      error({ statusCode: 404, message: 'We are sorry but the page ran away...' })
    }
  },
  data() {
    return {
      content: Object,
    }
  },
  created(){
    //this.fetchContent();
    
  },
  mounted(){
    //console.log('baseAPIUrl', process.env.baseAPIUrl) // world
    
  },
  methods: {
    async fetchContent() {
      //const content = await this.$axios.$get('/api/home-page')
      console.log("data", content)
      //this.content = content
    }
  }
}
</script>

<style scoped lang="scss">
.page-bg{
    background-color: $color-white;
  }
</style>
