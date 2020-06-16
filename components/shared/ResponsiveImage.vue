<template>
<div>
    <img v-if="imageX1" :srcset="
        `/api${imageX1.formats.thumbnail.url} ${imageX1.formats.thumbnail.width}w,
            ${imageX1.formats.small ? '/api' + imageX1.formats.small.url : ''} ${imageX1.formats.small ? imageX1.formats.small.width + 'w,' : ''}
            ${imageX1.formats.medium ? '/api' + imageX1.formats.medium.url : ''} ${imageX1.formats.medium ? imageX1.formats.medium.width + 'w,' : ''}
            ${imageX1.formats.large ? '/api' + imageX1.formats.large.url : ''} ${imageX1.formats.large ? imageX1.formats.large.width + 'w,' : ''}
            /api${imageX1.url} ${imageX1.width}w,
            ${imageX2 ? '/api' + imageX2.url : ''} ${imageX2 ? imageX2.width + 'w,' : ''}`"
        :sizes="sizes"
        :src="'/api' + imageX1.url"
        class="image"
        :alt="imageX1.alternativeText">
</div>
</template>

<script>
export default {
    props:{
        imageX1: {
            type: Object,
            required: true
        },
        imageX2: Object,
        imageX1mob: Object,
        imageX2mob: Object,
        sizes: {
            type: String,
            required: true
        },
    }
}
</script>

<style scoped lang="scss">
</style>
