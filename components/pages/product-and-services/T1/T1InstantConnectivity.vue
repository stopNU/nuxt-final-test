<template>
    <div class="outer-wrapper">
        <div class="inner-wrapper with-padding text-section">
          <div class="content-wrapper">
            <SharedTitleBlueUnderline 
                :title="data.section_title"
                :text="data.section_subtitle"
            />
            <div class="highlights">
                <div class="highlight" v-for="item in data.highlights" :key="item.id">
                  <img :src="'/api' + item.icon.url" alt="">
                  <p>{{item.text}}</p>
              </div>
            </div>
        </div><!-- .content-wrapper -->
    </div><!-- .inner-wrapper -->
        <div class="inner-wrapper with-padding">
            <div class="line"></div>
            <div class="tabs-wrapper">
                <h4 class="white">{{data.tab_section_title}}</h4>
                <el-tabs class="tabs" v-model="activeName" stretch>
                    <el-tab-pane v-for="tab in data.tab_item" :key="tab.id" lazy :label="tab.tab_label" :name="tab.tab_label">
                        <div class="tab-content white">{{tab.tab_content}}</div>
                    </el-tab-pane>
                </el-tabs>
            </div>
            <div class="line"></div>
        </div><!-- .inner-wrapper -->
    </div><!-- .outer-wrapper -->
</template>

<script>
export default {
    props:{
        data: Object
    },
    data() {
      return {
        activeName: this.data.tab_item[0].tab_label
      };
    }
}
</script>

<style scoped lang="scss">
    .text-section{
        padding-bottom: 0px;
        .content-wrapper{
            display: grid;
            grid-template-columns: 1fr 1fr;
            column-gap: 160px;
            @media screen and (max-width: $media-tablet) {
                column-gap: 30px;
            }
            @media screen and (max-width: $media-mobile) {
                grid-template-columns: 1fr;
                row-gap: 60px;
            }
        }
    }
    .tabs-wrapper{
        background-color: $bg-brand;
        padding: 40px 60px;
        @media screen and (max-width: $inner-wrapper) {
            padding: 60px $side-padding;
        }
        @media screen and (max-width: $media-mobile) {
            padding: 60px $side-padding-mobile;
        }
        h4{
            text-align: center;
            margin-bottom: 40px;
        }
        .tabs{
            max-width: $content-wrapper;
            margin: 0 auto;
            .tab-content{
                margin-top: 15px;
            }
        }
    }
    .highlights{
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        @media screen and (max-width: $media-mobile) {
            grid-template-columns: repeat(1, 1fr);
        }
        .highlight{
            display: grid;
            grid-template-columns: 36px 190px;
            align-items: center;
            margin-bottom: 20px;
        }
    }
</style>
