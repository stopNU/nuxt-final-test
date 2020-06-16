<template>
    <div>
        <div class="outer-wrapper">
            <div class="inner-wrapper">
                <div class="content-wrapper white content">
                    <div class="logos">
                        <div class="logo">
                            <img class="" 
                                srcset="
                                    ~/assets/logos/tag_logo_footer@2x.png 2x,
                                    ~/assets/logos/tag_logo_footer.png 1x"
                                src="~/assets/logos/tag_logo_footer.png">
                            <div class="vertical-line"></div>
                            <img class="" 
                                srcset="
                                    ~/assets/logos/sg_logo_footer@2x.png 2x,
                                    ~/assets/logos/sg_logo_footer.png 1x"
                                src="~/assets/logos/sg_logo_footer.png">
                        </div>
                        <div class="box">
                            <h6 class="white">Authorized Master Distributor of Secure Group</h6>
                        </div>
                    </div>
                    <div class="menu">
                        <ul>
                            <li><a href="#">About</a></li>
                            <li><a href="#">Menu2</a></li>
                            <li><a href="#">Menu3</a></li>
                            <li><a href="#">Menu4</a></li>
                            <li><a href="#">Menu5</a></li>
                            <li><a href="#">Menu6</a></li>
                            <li><a href="#">Menu7</a></li>
                            <li><a href="#">Menu8</a></li>
                        </ul>
                    </div>
                    <div class="address">
                        <div class="vertical-line"></div>
                        <div>
                            <span>ADDRESS</span><br> 
                            183-925 Maisonneuve Ouest,<br>
                            Montreal H3A 0A5,<br> 
                            Canada
                        </div>
                    </div>
                </div>
                <div class="copyright">

                </div>
            </div>
        </div>
     
        <div class="outer-wrapper blue-top-border">
            <div class="inner-wrapper">
                <div class="content-wrapper copyright">
                    <p class="white">© T.A.G. Consultation 2012-{{ new Date().getFullYear() }}. All Rights Reserved.</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped lang="scss">
    .copyright{
        padding: 15px 0 25px;
        @media screen and (max-width: $content-wrapper) {
            padding: 15px 30px 25px;
        }
        p{
            font-size: 0.75rem;
        }
    }
    .logos{
        display: flex;
        align-items: center;
        @media screen and (max-width: $media-mobile) {
            grid-column: span 2;
            display: grid;
            grid-template-columns: 1fr 1fr;
            
        }
        .logo{
            display: flex;
            align-items: center;
        }
        > img{
            align-self: center;
        }
        .vertical-line{
            margin: 0 15px;
            height: 30px;
        }
        .box{
            background-color: $color-brand-dark;
            padding: 6px 50px 6px 10px;
            margin-left: 15px;
            h6{
                max-width: 130px;
            }
        }
    }
    .outer-wrapper{
        background-color: #010B1B;
        &.blue-top-border{
            border-top: 1px solid $color-brand-dark;
        }
    }
    .content-wrapper.content{
        padding-top: 50px;
        padding-bottom: 95px;
        display: grid;
        grid-template-columns: 2fr 2fr 1fr;
        @media screen and (max-width: $media-mobile) {
            grid-template-columns: 1fr 1fr;
            row-gap: 30px;
            padding-top: 60px;
            padding-bottom: 30px;
        }
        align-items: center;
        .address{
            display: flex;
            align-items: center;
            font-size: 0.75rem;
            line-height: 1.6;
            @media screen and (max-width: $media-mobile) {
                line-height: 1.75;
            }
            span{
                font-size: 0.875rem;
            }
        }
    }
    .vertical-line{
        border-left: 1px solid $color-brand;
        margin-right: 15px;
        height: 65px;
        @media screen and (max-width: $media-mobile) {
            height: 85px;
        }
    }
    ul{
        list-style-type: none;
        columns: 2;
        list-style-position: inside;//this is important addition
        @media screen and (max-width: $media-mobile) {
            columns: 1;
            padding: 0px;
        }
        li{
            a{
                font-size: 0.875rem;
                font-weight: 400;
                line-height: 1.79;
                font-family: $font-headlines;
                color: $color-white;
                text-decoration: none;
                text-transform: uppercase;
                @media screen and (max-width: $media-mobile) {
                    line-height: 1.5;
                }
                &:hover{
                    color: $color-brand;
                }
            }
        }
    }
</style>
