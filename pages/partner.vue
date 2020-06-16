<template>
  <div class="container">
    <PartnerHeader v-if="content.header" :data="content.header" />
    <LazyPartnerPartnershipType v-if="content.partnership_type" :data="content.partnership_type" />
    <LazyPartnerWeSupportYou v-if="content.we_support_you" :data="content.we_support_you" />
    <div class="outer-wrapper with-padding">
      <div class="line"></div>
      <div class="inner-wrapper">
        <div class="form-wrapper">
          <SharedTitleBlueUnderline class="hide-mobile"
              title="Become a Partner"
          />
          <HubspotForm class="form fullwidth" title="Write us a message" formId="06bee465-28e3-474d-97e1-4e9bb3f1fc6e" />
        </div>
      </div><!-- .inner-wrapper -->
      <div class="line hide-mobile"></div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, error }) {
    try{
      const content = await $axios.$get('/api/partner-page')
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
  mounted(){
    //console.log('baseAPIUrl', process.env.baseAPIUrl) // world
    console.log("data", this.content)
  }
}
</script>

<style scoped lang="scss">
  .outer-wrapper{
    @media screen and (max-width: $media-mobile) {
      padding-bottom: 0px;
    }
  }
  .inner-wrapper{
    background-color: $bg-neutral;
  }
  .form-wrapper{
    max-width: $content-wrapper;
    margin: 0 auto;
    padding: 60px 0;
    @media screen and (max-width: $inner-wrapper) {
      padding: 60px $side-padding;
    }
    @media screen and (max-width: $media-mobile) {
      padding: 60px $side-padding-mobile;
    }
    .form{
      margin-top: 60px;
      @media screen and (max-width: $media-mobile) {
        margin-top: 0px;
      }
    }
  }
</style>
