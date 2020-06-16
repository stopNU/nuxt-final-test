<template>
    <div class="outer-wrapper">
      <div class="content">
        <div class="image-box">
          <ResponsiveImage v-if="data.image_desktop" 
            :imageX1="data.image_desktop.image_x1" 
            :imageX2="data.image_desktop.image_x2" 
            sizes="(max-width: 768px) 100vw, 50vw" />
        </div>
        <div class="info">
          <SharedTitleBlueUnderline
            :title="data.section_title"
            :text="data.section_subtitle"
          />
          <div class="list">
              <div class="list-item" v-for="item in data.sas_features" :key="item.id">
                  <img :src="'/api' + item.icon.url" alt="">
                  <p>{{item.text}}</p>
              </div>
          </div>
          <p>{{data.btn_teaser}}</p>
          <BrandButtonArrow class="btn" :url="data.btn.link">{{data.btn.text}}</BrandButtonArrow>
        </div>
      </div>
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
        background-color: $bg-neutral;
        .content{
            display: grid;
            grid-template-columns: 1fr $content-wrapper/2 $content-wrapper/2 1fr;
            align-items: center;
            column-gap: 140px;
            row-gap: 30px;
            padding: 250px 0;
            @media screen and (max-width: $inner-wrapper) {
                grid-template-columns: 1fr 1fr;
                column-gap: 30px;
            }
            @media screen and (max-width: $media-mobile) {
                grid-template-columns: 1fr;
                padding: $section-padding-mobile 0;
            }
        }
    }
    .image-box{
        grid-column-start: 1;
        grid-column-end: 3;
        @media screen and (max-width: $inner-wrapper) {
            grid-column-start: 1;
            grid-column-end: 1;
        }
        @media screen and (max-width: $media-mobile) {
            grid-row: 2;
        }
        img{
            max-width: 100%;
        }
    }
    .info{
        grid-column-start: 3;
        grid-column-end: 3;
        @media screen and (max-width: $inner-wrapper) {
            grid-column-start: 2;
            grid-column-end: 2;
            padding: 0 $side-padding;
        }
        @media screen and (max-width: $media-mobile) {
            grid-column-start: 1;
            grid-column-end: 1;
            padding: 0 $side-padding-mobile;
        }
        .list{
            margin-top: 20px;
            .list-item{
                display: grid;
                grid-template-columns: 36px 190px;
                align-items: center;
                margin-bottom: 20px;
            }
        }
        .btn{
            margin-top: 20px;
        }
    }
</style>
