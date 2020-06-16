<template>
    <div class="outer-wrapper">
    <div class="line"></div>
      <div class="inner-wrapper with-padding">
          <div class="content-wrapper">
              <SharedTitleBlueUnderline 
                  :title="data.section_title"
                  :text="data.section_subtitle"
              />
              <div class="features" v-if="data.features.length > 0">

                <div class="feature hide-mobile" v-for="item in data.features" :key="item.id">
                  <img :src="`/api${item.icon.url}`" :alt="item.icon.alternativeText">
                  <h4>{{item.title}}</h4>
                  <p>{{item.text}}</p>
                </div>

                <el-carousel class="carousel feature show-mobile"  
                  height="200px" 
                  indicator-position="outside"
                  arrow="never"
                  ref="carousel"
                  :autoplay="false" 
                  v-touch:swipe.right="swipeRightHandler" 
                  v-touch:swipe.left="swipeLeftHandler">
                  <el-carousel-item v-for="item in data.features" :key="item.id">
                      <div class="content">
                          <img :src="`/api${item.icon.url}`" :alt="item.icon.alternativeText">
                          <h4>{{item.title}}</h4>
                          <p>{{item.text}}</p>
                      </div>
                  </el-carousel-item>
                </el-carousel>

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
  methods: {
    swipeLeftHandler(){
      this.$refs.carousel.next()
    },
    swipeRightHandler(){
      this.$refs.carousel.prev()
    }
  }
}
</script>

<style scoped lang="scss">
  .features{
    margin-top: 20px;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    column-gap: 30px;
    row-gap: 30px;
    @media screen and (max-width: $media-mobile) {
        grid-template-columns: 1fr;
        margin-top: 60px;
    }
    .feature{
      h4{
        margin: 20px 0;
        line-height: 1.2;
        color: $color-brand-dark;
      }
    }
  }
</style>
