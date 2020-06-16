<template>
    <div class="outer-wrapper" v-bind:style="{ backgroundImage: `url(${'/api' + data.bg_image.url})` }">
        <div class="inner-wrapper with-padding">
            <div class="content-wrapper">
                <SharedTitleBlueUnderline 
                    :title="data.title"
                    :text="data.text"
                    :center="true"
                    :whiteText="true"
                />
                <BrandButton class="btn" :url="data.link_btn.link" v-if="data.link_btn">{{data.link_btn.text}}</BrandButton>
            </div><!-- .content-wrapper -->
        </div><!-- .inner-wrapper -->
    </div><!-- .outer-wrapper -->
</template>

<script>
export default {
    props:{
        data: Object,
    },
    mounted(){
        //console.log("homepageSpecial", this.data);
    },
}
</script>

<style scoped lang="scss">
    .outer-wrapper{
        background-repeat: no-repeat;
        background-size: cover;
    }
    .btn{
        margin-top: 45px;
        text-align: center;
    }
</style>
