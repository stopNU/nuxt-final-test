<template>
    <div class="outer-wrapper">
        <div class="inner-wrapper with-padding">
            <div class="content-wrapper">
                <div class="features">
                    <div class="feature" v-for="item in data.feature" :key="item.id">
                        <img :src="'/api' + item.icon.url" :alt="item.icon.alternativeText">
                        <h4>{{item.text}}</h4>
                    </div>
                </div>
            </div><!-- .content-wrapper -->
        </div><!-- .inner-wrapper -->
        <div class="line"></div>
    </div><!-- .outer-wrapper -->
</template>

<script>
export default {
    props:{
        data: Object,
    }
}
</script>

<style scoped lang="scss">
    .outer-wrapper{
        background-color: $bg-neutral;
    }
    .features{
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        column-gap: 30px;
        row-gap: 30px;
        text-align: center;
        @media screen and (max-width: $media-mobile) {
            grid-template-columns: repeat(1, 1fr);
            .feature{
                display: flex;
                flex-direction: row;
                align-items: center;
            }
            img{
                width: 60px;
            }
        }
        h4{
            margin-top: 45px;
            @media screen and (max-width: $media-mobile) {
                font-size: 24px;
                line-height: 36px;
                margin-top: 0px;
                margin-left: 25px;
            }
        }
    }
</style>
