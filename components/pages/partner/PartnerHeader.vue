<template>
    <FullscreenSection 
    class="fullscreen"
    v-if="data.bg_image.image_x1 && data.bg_image.image_x2"
    :imageX1="data.bg_image.image_x1" 
    :imageX2="data.bg_image.image_x2"
    bgcolor="#000000">
        <div class="inner-wrapper">
            <div class="content-wrapper fullscreen-content">
                <div class="info">
                    <h1 v-if="data.section_title" class="white">{{data.section_title}}</h1>
                    <p v-if="data.section_subtitle" class="subtitle white">{{data.section_subtitle}}</p>
                    <BrandButton :url="data.button.link" v-if="data.button.link">{{data.button.text}}</BrandButton>
                </div>
            </div><!-- .content-wrapper -->
        </div><!-- .inner-wrapper -->
    </FullscreenSection>
</template>

<script>
export default {
    props:{
        data: Object,
    }
}
</script>

<style scoped lang="scss">
    .inner-wrapper{
        align-items: center;
        display: grid;
        height: 100%;
        .content-wrapper{
            width: 100%;
        }
    }
    .info{
        max-width: 500px;
    }
</style>
