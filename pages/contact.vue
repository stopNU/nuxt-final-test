<template>
   <div class="outer-wrapper">
        <div class="inner-wrapper with-padding menu-padding">
            <div class="content-wrapper">
                <div class="info">
                    <SharedTitleBlueUnderline 
                        :title="content.section_title"
                        :text="content.section_subtitle"
                        class="title"
                    />
                    <div class="phone" v-if="content.phone_number">
                        <h5>Call us:</h5>
                        <p>{{content.phone_number}}</p>
                    </div>
                    <div class="email" v-if="content.email">
                        <h5>Text us:</h5>
                        <p><a :href="`mailto:${content.email}`">{{content.email}}</a></p>
                    </div>
                    <div class="address" v-if="content.address">
                        <h5>Our address:</h5>
                        <p>{{content.address}}</p>
                    </div>
                    <div class="social-media" v-if="content.social_media.length > 0">
                        <h5>Follow us:</h5>
                        <div v-for="item in content.social_media" :key="item.id">
                            <a :href="item.url" target="_blank"><img :src="'/api' + item.icon.url" :alt="item.icon.alternativeText"></a>
                        </div>
                    </div>
                </div>
                <div class="form">
                    <HubspotForm :title="content.form_title" :formId="content.hubspot_form_id" />
                </div>
            </div><!-- .content-wrapper -->
        </div><!-- .inner-wrapper -->
    </div><!-- .outer-wrapper -->
</template>

<script>
export default {
    async asyncData({ $axios, error }) {
        try{
            const content = await $axios.$get('/api/contact-page')
            return { content }
        } catch(e) {
            console.log("error", e);
            error({ statusCode: 404, message: 'We are sorry but the page ran away...' })
        }
    },
    data() {
        return {
            content: Object
        }
    }
}
</script>

<style scoped lang="scss">
    .outer-wrapper{
        background-color: $bg-neutral;
    }
    div.inner-wrapper{
        .content-wrapper{
            display: grid;
            grid-template-columns: 5fr 7fr;
            column-gap: 30px;
            @media screen and (max-width: $media-mobile) {
                grid-template-columns: 1fr;
                row-gap: 60px;
            }
        }
    }
    .info{
        padding-right: 100px;
        @media screen and (max-width: $media-mobile) {
            display: grid;
            grid-template-columns: 1fr 1fr;
            column-gap: 30px;
        }
        .title{
            margin-bottom:30px;
            grid-column: span 2;
        }
        .phone, .address, .email{
            max-width: 200px;
            margin-bottom: 20px;
        }
        .social-media{
            div{
                display: inline-block;
                margin-right: 15px;
            }
            img{
                width: 24px;
                height: 24px;
            }
        }
    }
</style>
