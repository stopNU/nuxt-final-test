<template>
    <div class="btn">
        <!--<a :href="`${url}`" :target="openInTab ? '_blank' : ''"><slot></slot></a>-->
        <nuxt-link :target="openInTab ? '_blank' : ''" :to="{ path: `${url}` }"><slot></slot></nuxt-link>
    </div>
</template>

<script>
export default {
    props:{
        url: String,
        openInTab: Boolean
    },
}
</script>

<style scoped lang="scss">

</style>
