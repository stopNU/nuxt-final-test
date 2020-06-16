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
    .btn{
        a{
            background-color: transparent;
            border: 1px solid $color-brand;
            color: $color-brand;
            font-weight: 700;
            padding: 8px 12px;
        }
        &.white a{
            color: $color-white;
            border: 1px solid $color-white;
        }
    }
</style>
