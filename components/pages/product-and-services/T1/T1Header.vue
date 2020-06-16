<template>
  <FullscreenSection 
    class="fullscreen"
    v-if="data.bg_image.image_x1 && data.bg_image.image_x2"
    :imageX1="data.bg_image.image_x1" 
    :imageX2="data.bg_image.image_x2"
    bgcolor="#000000">
    <div class="inner-wrapper with-padding menu-padding">
      <div class="content-wrapper hide-mobile fullscreen-content">
        <div class="info">
          <h1 v-if="data.section_title" class="white">{{data.section_title}}</h1>
          <p v-if="data.section_description" class="subtitle white">{{data.section_description}}</p>
          <BrandButton :url="data.btn_url" v-if="data.btn_label">{{data.btn_label}}</BrandButton>
        </div>
        <div class="image">
          <ResponsiveImage v-if="data.phone.image_x1" class="image"
            :imageX1="data.phone.image_x1" 
            :imageX2="data.phone.image_x2" 
            sizes="(max-width: 768px) 50vw, 400px" />
        </div>
      </div><!-- .content-wrapper -->
    
      <div class="content-wrapper show-mobile fullscreen-content">
        <el-carousel class="carousel" height="100vh" 
          direction="vertical"
          ref="carousel"
          :loop="false"
          v-touch:swipe.top="swipeTopHandler" 
          v-touch:swipe.bottom="swipeBottomHandler" 
          :autoplay="false">
          <el-carousel-item>
            <div class="info">
              <h1 v-if="data.section_title" class="white">{{data.section_title}}</h1>
              <p v-if="data.section_description" class="subtitle white">{{data.section_description}}</p>
              <BrandButton :url="data.btn_url" v-if="data.btn_label">{{data.btn_label}}</BrandButton>
            </div>
          </el-carousel-item>
          <el-carousel-item>
            <div class="image">
              <h1 v-if="data.section_title" class="white">{{data.section_title}}</h1>
              <ResponsiveImage v-if="data.phone.image_x1" class="image"
                :imageX1="data.phone.image_x1" 
                :imageX2="data.phone.image_x2" 
                sizes="(max-width: 768px) 80vw, 400px" />
            </div>
          </el-carousel-item>
        </el-carousel>
      </div><!-- .content-wrapper -->

    </div><!-- .inner-wrapper -->
  </FullscreenSection>
</template>

<script>
export default {
  props:{
    data: Object
  },
  data() {
    return {
      test: 'green',
    }
  },
  methods: {
    swipeTopHandler(){
      this.$refs.carousel.next()
    },
    swipeBottomHandler(){
      this.$refs.carousel.prev()
    }
  }
}
</script>

<style scoped lang="scss">
  .fullscreen{
    @media screen and (min-width: $media-tablet) {
      min-height: 900px;
    }
  }
  .inner-wrapper{
    height: 100%;
    @media screen and (max-width: $media-mobile) {
      padding: 0;
    }
    .content-wrapper{
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
      column-gap: 30px;
      height: 100%;
      @media screen and (max-width: $media-mobile) {
        grid-template-columns: 1fr;
        .info, .image{
          @media screen and (max-width: $media-mobile) {
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
          }
        }
      }
    }
  }
  div.image{
    text-align: right;
    @media screen and (max-width: $media-mobile) {
      text-align: center;
      padding: 100px 0;
      h1{
        margin-bottom: 30px;
      }
    }
  }
</style>
