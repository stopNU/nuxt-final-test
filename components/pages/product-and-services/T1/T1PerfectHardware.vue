<template>
    <div class="outer-wrapper">
      <div class="content">
        <div class="info">
          <SharedTitleBlueUnderline
            :title="data.section_title"
            :text="data.section_subtitle"
          />
          <Accordian class="accordian"
            :data="data.list_expand_items" 
            v-if="data.list_expand_items && data.list_expand_items.length > 0" />
        </div>

        <div class="line-wrapper show-mobile"><div class="line"></div></div>
        <div class="image-box">
          <ResponsiveImage v-if="data.image" 
            :imageX1="data.image.image_x1" 
            :imageX2="data.image.image_x2" 
            sizes="(max-width: 768px) 100vw, 50vw" />
        </div>
        <div class="line-wrapper show-mobile"><div class="line"></div></div>

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
    .content{
        display: grid;
        grid-template-columns: 1fr $content-wrapper/2 $content-wrapper/2 1fr;
        column-gap: 30px;
        padding: 250px 0 250px;
        @media screen and (max-width: $inner-wrapper) {
            grid-template-columns: 1fr 1fr;
        }
        @media screen and (max-width: $media-mobile) {
            grid-template-columns: 1fr;
            padding: $section-padding-mobile 0;
        }
    }
  }
  .image-box{
    grid-column-start: 3;
    grid-column-end: 5;
    background-color: $bg-brand;
    border: 10px solid $color-brand;
    border-right-width: 0px;
    display: flex;
    @media screen and (max-width: $inner-wrapper) {
      grid-column-start: 2;
      grid-column-end: 2;
    }
    @media screen and (max-width: $media-mobile) {
      grid-column-start: 1;
      grid-column-end: 1;
      border: 0px;
    }
    img{
      width: 100%;
    }
  }
  .info{
    grid-column-start: 2;
    grid-column-end: 3;
    max-width: 400px; 
    min-height: 490px;
    @media screen and (max-width: $inner-wrapper) {
      grid-column-start: 1;
      grid-column-end: 1;
      padding: 0 $side-padding;
    }
    @media screen and (max-width: $media-mobile) {
      min-height: auto;
      margin-bottom: 30px;
      padding: 0 $side-padding-mobile;
    }
    .accordian{
      padding-top: 25px;
    }
  }
</style>
