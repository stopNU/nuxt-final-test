<template>
    <div class="outer-wrapper">
        <div class="line"></div>
        <div class="inner-wrapper with-padding">
            <div class="content-wrapper">
                <SharedTitleBlueUnderline 
                    title="Featured Articles"
                    text="text text text"
                />
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
        //console.log("homepageArticles", this.data);
    },
}
</script>

<style scoped lang="scss">
    .outer-wrapper{
        background-color: $color-white;
    }
</style>
