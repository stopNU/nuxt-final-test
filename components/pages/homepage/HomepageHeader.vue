<template>
    <div class="outer-wrapper fullscreen-bg">
        <video playsinline autoplay muted loop poster="http://localhost:1337/uploads/video_placeholder_300x176_c423494ad9.png" id="bgvideo" width="x" height="y">
            <source :src="'/api/' + data.bg_video.url" type="video/mp4">
        </video>
        <div class="inner-wrapper">
            <div class="carousel-wrapper">
                <div class="line"></div>
                <el-carousel class="homepage-carousel">
                    <el-carousel-item v-for="item in data.homepage_slider" :key="item.id">
                        <div class="content">
                            <h1 class="white">{{ item.title }}</h1>
                            <p class="white">{{ item.subtitle }}</p>
                            <BrandButton :url="item.link_btn.link" v-if="item.link_btn">{{item.link_btn.text}}</BrandButton>
                        </div>
                    </el-carousel-item>
                </el-carousel>
                <div class="line"></div>
            </div>
            <!--<div class="content-wrapper">
                
            </div>-->
        </div>
    </div>
</template>

<script>
export default {
    props:{
        data: Object,
    },
    mounted(){
        //console.log("homepageheader", this.data);
    },
    methods: {
        
    }
}
</script>

<style scoped lang="scss">
    .outer-wrapper{
        overflow: hidden;
        .inner-wrapper{
            height: inherit;
        }
    }
    
    video#bgvideo {
        position: fixed;
        top: 0px;
        left: 0px;
        min-width: 100%;
        min-height: 100%;
        width: auto;
        height: auto;
        z-index: -1;
        overflow: hidden;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .inner-wrapper{
        display: grid;
        align-items: center;
        height: inherit;
    }
    .homepage-carousel{
        background-color:rgba(1, 11, 27, 0.5);
        .content{
            max-width: 480px;
            margin: 0 auto;
            text-align: center;
            display: flex;
            align-items: center;
            height: 100%;
            justify-content: center;
            flex-direction: column;
            p{
                margin: 20px 0 45px;
            }
        }
    }
</style>
