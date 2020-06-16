<template>
    <div class="outer-wrapper">
        <div class="content">
            <div class="line-wrapper show-mobile"><div class="line"></div></div>

            <div class="image-wrapper">
                <ResponsiveImage v-if="activeListItem"
                    :imageX1="activeListItem.image_x1 ? activeListItem.image_x1 : data.list_expand_item[0].image_x1" 
                    :imageX2="activeListItem.image_x2 ? activeListItem.image_x2 : data.list_expand_item[0].image_x2" 
                    sizes="(max-width: 768px) 90vh, 630px" />
                <ResponsiveImage v-else
                    :imageX1="data.list_expand_item[0].image_x1" 
                    :imageX2="data.list_expand_item[0].image_x2" 
                    sizes="(max-width: 768px) 90vh, 630px" />
            </div>

            <div class="line-wrapper show-mobile"><div class="line"></div></div>
            <div class="info">
                <SharedTitleBlueUnderline :title="data.section_title" />
                <Accordian class="accordian" 
                    @changeActive="handleChange"
                    :activeName="activeName" 
                    :data="data.list_expand_item" 
                    v-if="data.list_expand_item.length > 0" />
            </div>
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
        background-color: $bg-neutral;
        .content{
            display: grid;
            grid-template-columns: 1fr $content-wrapper/2 $content-wrapper/2 1fr;
            column-gap: 30px;
            padding: 270px 0 100px;
            @media screen and (max-width: $inner-wrapper) {
                grid-template-columns: 1fr 1fr;
            }
            @media screen and (max-width: $media-mobile) {
                grid-template-columns: 1fr;
                padding: 190px 0 $section-padding-mobile;
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
        border-left-width: 0px;
        grid-column-start: 1;
        grid-column-end: 3;
        .image{
            position: absolute;
            max-height: 700px;
            max-width: 100%;
            @media screen and (max-width: $media-mobile) {
                max-height: 500px;
            }
        }
        @media screen and (max-width: $inner-wrapper) {
            grid-column-start: 1;
            grid-column-end: 1;
        }
        @media screen and (max-width: $media-mobile) {
            align-items: flex-end;
            height: 280px;
            border: 0px;
        }
    }
    .info{
        grid-column-start: 3;
        grid-column-end: 3;
        min-height: 540px;
        @media screen and (max-width: $inner-wrapper) {
            grid-column-start: 2;
            grid-column-end: 2;
        }
        @media screen and (max-width: $media-mobile) {
            grid-column-start: 1;
            grid-column-end: 1;
            margin-top: 30px;
            padding: 0 $side-padding-mobile;
            min-height: auto;
        }
        .accordian{
            padding-top: 15px;
        }
    }
</style>
