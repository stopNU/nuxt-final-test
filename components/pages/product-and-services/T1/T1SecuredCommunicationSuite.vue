<template>
    <div class="outer-wrapper">
        <div class="content">
            <div class="info">
                <SharedTitleBlueUnderline :title="data.section_title" :text="data.section_subtitle" />
                <Accordian class="accordian" 
                    @changeActive="handleChange"
                    :activeName="activeName" 
                    :data="data.list_expand_item" 
                    v-if="data.list_expand_item.length > 0" />
            </div>
            <div class="line-wrapper show-mobile"><div class="line"></div></div>

            <div class="image-wrapper">
                <ResponsiveImage v-if="activeListItem" class="image"
                    :imageX1="activeListItem.image_x1 ? activeListItem.image_x1 : data.list_expand_item[0].image_x1" 
                    :imageX2="activeListItem.image_x2 ? activeListItem.image_x2 : data.list_expand_item[0].image_x2" 
                    sizes="(max-width: 768px) 70vw, 700px" />
                <ResponsiveImage v-else class="image"
                    :imageX1="data.list_expand_item[0].image_x1" 
                    :imageX2="data.list_expand_item[0].image_x2" 
                    sizes="(max-width: 768px) 70vw, 700px" />
            </div>

            <div class="line-wrapper show-mobile"><div class="line"></div></div>
        </div>
    </div><!-- .outer-wrapper -->
</template>

<script>
export default {
    props:{
        data: Object
    },
    data() {
        return {
            activeName: this.data.list_expand_item[0].id ? this.data.list_expand_item[0].id : '0'
        }
    },
    computed: {
        activeListItem: function () {
           return this.data.list_expand_item.find(item => item.id === this.activeName)
        }
    },
    methods: {
        handleChange(value) {
            this.activeName = value;
        }
    }
}
</script>

<style scoped lang="scss">
    .outer-wrapper{
        overflow: hidden;
        .content{
            display: grid;
            grid-template-columns: 1fr $content-wrapper/2 $content-wrapper/2 1fr;
            column-gap: 30px;
            padding: 250px 0;
            @media screen and (max-width: $inner-wrapper) {
                grid-template-columns: 1fr 1fr;
            }
            @media screen and (max-width: $media-mobile) {
                grid-template-columns: 1fr;
                padding: $section-padding-mobile 0 $section-padding-mobile+30px;
            }
        }
    }
    .image-wrapper{
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        background-color: $bg-brand;
        height: 390px;
        width: 100%;
        border: 10px solid $color-brand;
        border-right-width: 0px;
        grid-column-start: 3;
        grid-column-end: 5;
        .image{
            position: relative;
            top: 50px;
        }
        @media screen and (max-width: $inner-wrapper) {
            grid-column-start: 2;
            grid-column-end: 2;
        }
        @media screen and (max-width: $media-mobile) {
            grid-column-start: 1;
            grid-column-end: 1;
            border: 0px !important;
            height: 220px;
        }
    }
    .info{
        grid-column-start: 2;
        grid-column-end: 3;
        max-width: 450px; 
        min-height: 490px;
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
        .accordian{
            padding-top: 25px;
        }
    }
</style>
