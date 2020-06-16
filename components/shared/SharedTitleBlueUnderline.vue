<template>
    <div class="component-content" v-bind:class="{ center: center }">
        <h2 v-bind:class="{ white: whiteText }">{{title}}</h2>
        <div class="line"></div>
        <p v-bind:class="{ white: whiteText }" v-if="text">{{text}}</p>
    </div>
</template>

<script>
export default {
    props:{
        title: String,
        text: String,
        center: Boolean,
        whiteText: Boolean
    },
}
</script>

<style scoped lang="scss">
    .component-content{
        max-width: 650px;
    }
    .line{
        margin: 15px 0 20px;
        height: 6px;
        width: 175px;
        background-color: $color-brand;
    }
    .center{
        text-align: center;
        margin: 0 auto;
        .line{
            margin-left: auto;
            margin-right: auto;
        }
    }
</style>
