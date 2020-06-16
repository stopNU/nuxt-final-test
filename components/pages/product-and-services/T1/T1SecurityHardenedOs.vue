<template>
    <div class="outer-wrapper" :style="cssProps">
      <div class="inner-wrapper with-padding text-wrapper">
        <div class="content-wrapper">
          <SharedTitleBlueUnderline class="intro"
              :title="data.section_title"
              :text="data.section_subtitle"
          />
        </div><!-- .content-wrapper -->
      </div><!-- .inner-wrapper -->
      <div class="line"></div>
      <div class="inner-wrapper with-padding box-wrapper">
        <div class="content-wrapper">
          <div class="content">
              <div class="list-item" v-for="item in data.os_security_list" :key="item.id">
                <h5 class="white">{{item.title}}</h5>
                <p class="white">{{item.text}}</p>
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
    data: Object
  },
  computed: {
    cssProps() {
        return {
            '--bg-image-x2': `url(/api${this.data.bg_image.image_x2.url})`,
            '--bg-image-x1': `url(/api${this.data.bg_image.image_x1.url})`,
            '--bg-image-large': this.data.bg_image.image_x1.formats.large ? `url(/api${this.data.bg_image.image_x1.formats.large.url})` : `url(/api${this.data.bg_image.image_x1.url})`,
            '--bg-image-medium': this.data.bg_image.image_x1.formats.large ? `url(/api${this.data.bg_image.image_x1.formats.medium.url})` : `url(/api${this.data.bg_image.image_x1.url})`,
            '--bg-image-small': this.data.bg_image.image_x1.formats.large ? `url(/api${this.data.bg_image.image_x1.formats.small.url})` : `url(/api${this.data.bg_image.image_x1.url})`,
        }
    }
  }
}
</script>

<style scoped lang="scss">
  .outer-wrapper{
    background-color: $bg-neutral;
    padding-bottom: 60px;
    background-image: var(--bg-image-x1);  
    background-repeat: no-repeat;
    background-position: 110% 0%;
    background-size: 800px;
    @media 
          (-webkit-min-device-pixel-ratio: 2), 
          (min-resolution: 192dpi) { 
          background-image: var(--bg-image-x2);  
      }
      @media screen and (max-width: 1000px) {
          background-image: var(--bg-image-large);  
      }
      @media screen and (max-width: $media-mobile) {
          background-image: var(--bg-image-medium);  
          background-position: 117% 0%;
          background-size: 300px;
      }
      @media screen and (max-width: 500px) {
          background-image: var(--bg-image-small);  
      }
  }
  .text-wrapper{
    padding-bottom: 0px;
    margin-bottom: 40px;
    .content-wrapper .intro{
      max-width: 400px;
    }
  }
  .box-wrapper{
    background-color: $color-brand-dark;
    padding: 40px 0;
    .content{
      display: grid;
      grid-template-columns: repeat( auto-fit, minmax(350px, 1fr) );
      column-gap: 60px;
      row-gap: 40px;
      @media screen and (max-width: $media-mobile) {
        grid-template-columns: 1fr;
      }
      h5{
        @media screen and (max-width: $media-mobile) {
          font-size: 1.5rem;
        }
      }
      p{
        font-family: $font-paragraphs-alt;
        line-height: 1.3;
        margin-top: 20px;
      }
    }
  }
</style>
