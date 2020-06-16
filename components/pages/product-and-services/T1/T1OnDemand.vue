<template>
    <div class="outer-wrapper">
        <div class="inner-wrapper with-padding">
            <div class="content-wrapper">
              <div class="intro">
                  <h4 class="white">{{data.section_title}}</h4>
                  <p class="white">{{data.section_subtitle}}</p>
              </div>
              <div class="customizations">
                  <h5 class="white" v-for="item in data.customizations" :key="item.id">{{item.text}}</h5>
              </div>
              <BrandButtonArrow class="btn white" :url="data.button.link">{{data.button.text}}</BrandButtonArrow>
            </div><!-- .content-wrapper -->
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
    .outer-wrapper{
        background-color: $color-brand-dark;
    }
    .btn{
        text-align: center;
    }
    .customizations{
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        column-gap: 30px;
        margin: 50px 0 40px;
        text-align: center;
        @media screen and (max-width: $media-mobile) {
            grid-template-columns: 1fr;
            row-gap: 60px;
            max-width: 250px;
            margin: 50px auto 30px;
        }
    }
    .intro{
        max-width: 400px;
        margin: 0 auto;
        text-align: center;
        h4{
            margin-bottom: 20px;
        }
        p{
            font-family: $font-paragraphs-alt;
            max-width: 350px;
            margin: 0 auto;
        }
    }
</style>
