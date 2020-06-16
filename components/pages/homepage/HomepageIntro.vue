<template>
    <div class="outer-wrapper">
        <div class="line center"></div>
        <div class="inner-wrapper with-padding">
            <div class="content-wrapper">
                <SharedTitleBlueUnderline 
                    :title="this.data.section_title"
                    :text="this.data.section_subtitle"
                />
                <div class="cards">
                    <el-card :body-style="{ padding: '0px' }" v-for="item in data.image_link_boxes" :key="item.id" >
                        <a :href="item.link">
                            <!--<img :src="'/api' + item.image.url" class="image">-->
                            <img :srcset="
                                `/api${item.image.formats.thumbnail.url} ${item.image.formats.thumbnail.width}w,
                                 ${item.image.formats.small ? '/api' + item.image.formats.small.url : ''} ${item.image.formats.small ? item.image.formats.small.width + 'w,' : ''}
                                 ${item.image.formats.medium ? '/api' + item.image.formats.medium.url : ''} ${item.image.formats.medium ? item.image.formats.medium.width + 'w,' : ''}
                                 ${item.image.formats.large ? '/api' + item.image.formats.large.url : ''} ${item.image.formats.large ? item.image.formats.large.width + 'w,' : ''}
                                 /api${item.image.url} ${item.image.width}w,`"
                                sizes="(max-width: 768px) 90vh, 400px"
                                :src="'/api' + item.image.url"
                                class="image"
                                :alt="item.image.alternativeText">
                            <div>
                                <h5 class="white">{{item.title}}</h5>
                            </div>
                        </a>
                    </el-card>
                </div>
            </div><!-- .content-wrapper -->
        </div><!-- .inner-wrapper -->
        <div class="line center"></div>
    </div><!-- .outer-wrapper -->
</template>

<script>
export default {
    props:{
        data: Object,
    },
    mounted(){
        console.log("homepageintro", this.data);
    },
}
</script>

<style scoped lang="scss">
    .cards{
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        column-gap: 30px;
        margin-top: 60px;
        @media screen and (max-width: $media-mobile) {
            grid-template-columns: repeat(1, 1fr);
            row-gap: 30px;
        }
        > div{
            border-radius: 0;
            background-color: $color-headlines;
            text-align: center;
            &:hover{
                background-color: $color-brand;
            }
        }
        a{
            text-decoration: none;
            img{
                @media screen and (max-width: $media-mobile) {
                    width: 100%;
                }
            }
        }
        h5{
            padding: 20px 0;
        }
    }
    .outer-wrapper{
        background-color: #FFFFFF;
    }
</style>
