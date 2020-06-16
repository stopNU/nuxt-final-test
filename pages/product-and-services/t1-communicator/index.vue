<template>
  <div class="container">
    <T1Header v-if="content.header" :data="content.header" />
    <LazyT1Intro v-if="content.intro" :data="content.intro" />
    <LazyT1LayeredSecurity v-if="content.layered_security" :data="content.layered_security" />
    <LazyT1SecuredCommunicationSuite v-if="content.secure_communication_suite" :data="content.secure_communication_suite" />
    <LazyT1SecurityHardenedOs v-if="content.security_hardened_os" :data="content.security_hardened_os" />
    <LazyT1PerfectHardware v-if="content.perfect_hardware" :data="content.perfect_hardware" />
    <LazyT1Sas v-if="content.t1_sas" :data="content.t1_sas" />
    <LazyT1InstantConnectivity v-if="content.instant_connectivity" :data="content.instant_connectivity" />
    <LazyT1OnDemand v-if="content.on_demand_customization" :data="content.on_demand_customization" />
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, error }) {
    try {
      const content = await $axios.$get('/api/t-1-communicator-page')
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
  }
}
</script>

<style scoped lang="scss">
  
</style>
