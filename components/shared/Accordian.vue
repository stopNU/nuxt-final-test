<template>
    <el-collapse v-model="activeListItem" accordion @change="handleChange">
        <div class="wrapper-collapse-item" v-for="item in data" :key="item.id">
            <i class="el-collapse-item__arrow el-icon-arrow-right" v-bind:class="{ 'is-active': item.id === activeListItem }"></i>
            <el-collapse-item :title="item.title" :name="item.id">
                <p>{{item.text}}</p>
                <BrandButtonArrow v-if="item.btn_label" :url="item.btn_url">{{item.btn_label}}</BrandButtonArrow>
            </el-collapse-item>
        </div>
    </el-collapse>
</template>

<script>
export default {
    props:{
        data: Array,
        activeName: [String, Number]
    },
    computed: {
        activeListItem: {
           get(){
             return this.activeName
           },
           set(newValue){
             return newValue
           } 
        }
    },
    methods:{
        handleChange(value){
            this.$emit('changeActive', value);
        }
    }
}
</script>

<style scoped lang="scss">
    .el-collapse{
        border: 0px;
        font-size: 0.75rem;
        font-weight: 700;
        .wrapper-collapse-item{
            display: flex;
            position: relative;
            .btn{
                margin-top: 15px;
            }
            i{
                position: absolute;
                top: 18px;
                font-size: 0.75rem;
                font-weight: 700;
            }
            .el-collapse-item{
                flex:1;
                padding-left: 25px;
            }
            .el-collapse-item__arrow.is-active{
                color: $color-brand-dark;
            }
        }
    }
</style>
