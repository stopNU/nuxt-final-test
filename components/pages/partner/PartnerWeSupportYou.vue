<template>
    <div class="outer-wrapper">
        <div class="content">
             <div class="info">
                <SharedTitleBlueUnderline v-if="this.data"
                    :title="data.section_title"
                    :text="data.section_subtitle"
                />
             </div>
             <div class="image-wrapper">
                <div class="line-wrapper show-mobile"><div class="line"></div></div>
                <picture class="image">
                    <source :srcset="`/api${data.image.image_x1_mob.url}, /api${data.image.image_x2_mob.url} 2x`"
                            media="(max-width: 768px)">
                    <source :srcset="`/api${data.image.image_x1.url}, /api${data.image.image_x2.url} 2x`"
                            media="(min-width: 769px)">
                    <img :src="`/api${data.image.image_x1.url}`" :alt="data.image.image_x1.alternativeText"
                        :srcset="`/api${data.image.image_x1.url}, /api${data.image.image_x2.url} 2x`">
                </picture>
                <div class="line-wrapper show-mobile"><div class="line"></div></div>
            </div>
        </div>
    </div><!-- .outer-wrapper -->
</template>

<script>
export default {
    props:{
        data: Object
    },
    mounted(){
        console.log("partner WE", this.data);
    }
}
</script>

<style scoped lang="scss">
    .outer-wrapper{
        overflow: hidden;
        background-color: $bg-neutral;
        .content{
            display: grid;
            grid-template-columns: 1fr $content-wrapper/2 $content-wrapper/2 1fr;
            align-items: center;
            column-gap: 30px;
            padding: 220px 0;
            @media screen and (max-width: $inner-wrapper) {
                grid-template-columns: 1fr 1fr;
            }
            @media screen and (max-width: $media-mobile) {
                grid-template-columns: 1fr;
                padding: $section-padding-mobile 0 $section-padding-mobile;
            }
        }
    }
    .image-wrapper{
        grid-column-start: 3;
        grid-column-end: 5;
        @media screen and (max-width: $inner-wrapper) {
            grid-column-start: 2;
            grid-column-end: 2;
        }
        @media screen and (max-width: $media-mobile) {
            grid-column-start: 1;
            grid-column-end: 1;
            border: 0px !important;
            background-color: transparent;
        }
        .image{
            border: 10px solid $color-brand;
            background-color: $color-headlines;
            border-right-width: 0px;
            width: 100%;
            display: block;
            img{
                width: 100%;
            }
            @media screen and (max-width: $media-mobile) {
                border: 0px;
                display: block;
            }
        }
        
    }
    .info{
        grid-column-start: 2;
        grid-column-end: 3;
        max-width: 480px;
        @media screen and (max-width: $inner-wrapper) {
            grid-column-start: 1;
            grid-column-end: 1;
            padding: 0 $side-padding;
        }
        @media screen and (max-width: $media-mobile) {
            min-height: auto;
            margin-bottom: $section-padding-mobile;
            padding: 0 $side-padding-mobile;
        }
    }
</style>
