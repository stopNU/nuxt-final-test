<template>
  <div class="outer-wrapper fullscreen-bg" :style="cssProps">
    <slot></slot>
  </div>
</template>

<script>
export default {
  props:{
    imageX1: Object,
    imageX2: Object,
    bgcolor: String,
  },
  computed: {
    cssProps() {
        return {
            'backgroundColor': this.bgcolor,
            '--bg-image-x2': `url(/api${this.imageX2.url})`,
            '--bg-image-x1': `url(/api${this.imageX1.url})`,
            '--bg-image-large': `url(/api${this.imageX1.formats.large.url})`,
            '--bg-image-medium': `url(/api${this.imageX1.formats.medium.url})`,
            '--bg-image-small': `url(/api${this.imageX1.formats.small.url})`,
        }
    }
  }
}
</script>

<style scoped lang="scss">
    .fullscreen-bg{
        background-image: var(--bg-image-x1);  
        @media 
            (-webkit-min-device-pixel-ratio: 2), 
            (min-resolution: 192dpi) { 
            background-image: var(--bg-image-x2);  
        }
        @media screen and (max-width: 1000px) {
            background-image: var(--bg-image-large);  
        }
        @media screen and (max-width: 750px) {
            background-image: var(--bg-image-medium);  
        }
        @media screen and (max-width: 500px) {
            background-image: var(--bg-image-small);  
        }
    }
</style>
