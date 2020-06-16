<template>
    <div class="outer-wrapper">
        <div class="inner-wrapper with-padding">
            <div class="content-wrapper">
                <SharedTitleBlueUnderline 
                    :title="this.data.section_title"
                />
            </div><!-- .content-wrapper -->
        </div><!-- .inner-wrapper -->
        <div class="inner-wrapper partner-types-wrapper">
            <div class="partner-types">
                <div class="partner-type" v-for="type in data.partner_types" :key="type.id">
                    <img v-if="type.icon" :src="'/api' + type.icon.url" alt="">
                    <h5>{{type.title}}</h5>
                    <p>{{type.text}}</p>
                </div>
            </div>
            <div class="btn-wrapper">
                <BrandButtonArrow class="btn" :url="data.button.link">{{data.button.text}}</BrandButtonArrow>
            </div>
        </div><!-- .inner-wrapper -->
    </div><!-- .outer-wrapper -->
</template>

<script>
export default {
    props:{
        data: Object
    }
}
</script>

<style scoped lang="scss">
    .partner-types-wrapper{
        padding-bottom: 120px;
        @media screen and (max-width: $media-mobile) {
            background-color: $bg-neutral;
            padding-bottom: 60px;
        }
    }
    .btn-wrapper{
        max-width: $content-wrapper;
        margin: 30px auto 0;
        @media screen and (max-width: $content-wrapper) {
            padding: 0 $side-padding;
        }
        @media screen and (max-width: $media-mobile) {
            padding: 0 $side-padding-mobile;
            margin: 10px auto 0;
        }
    }
    .partner-types{
        background-color: $bg-neutral;
        padding: 20px $side-padding;
        @media screen and (max-width: $media-mobile) {
            padding: 40px $side-padding-mobile 0;
        }
        .partner-type{
            max-width: $content-wrapper;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 20px 2fr 3fr;
            column-gap: 20px;
            align-items: center;
            padding: 20px 0;
            &:not(:last-child){
                border-bottom: 1px solid #707070;
            }
            @media screen and (max-width: $media-mobile) {
                grid-template-columns: 20px 1fr;
                padding: 20px 0 30px;
                p{
                    grid-column: span 2;
                    margin-top: 30px;
                }
            }
        }
    }
</style>
