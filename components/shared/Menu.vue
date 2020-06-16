<template>
    <div class="menu-wrapper" :class="{ 'navbar--hidden': !showNavbar }">
        <div class="inner-wrapper">
            <div class="content-wrapper">
              <div class="logo">
                <nuxt-link :to="{ path: '/' }"><img v-on:click="handleLogoClicked" src="~/assets/logos/logo_nav_desk.svg"></nuxt-link>
              </div>
              <el-menu
                  :default-active="activeIndex"
                  class="el-menu"
                  mode="horizontal"
                  @select="handleSelect"
                  text-color="#FFFFFF"
                  background-color="transparent"
                  >
                  <template v-for="item in menu.menu_item">
                    <el-menu-item :index="item.id.toString()" :key="item.id" v-if="item.submenu_item.length === 0">
                      <nuxt-link :to="{ path: item.url }">{{item.label}}</nuxt-link>
                    </el-menu-item>
                    <el-submenu :index="item.id.toString()" :key="item.id" v-if="item.submenu_item.length > 0" >
                        <template slot="title">{{item.label}}</template>
                        <el-menu-item v-for="subitem in item.submenu_item" :index="item.id.toString() + '.' + subitem.id.toString()" :key="subitem.id">
                          <nuxt-link :to="{ path: item.url + subitem.url }">{{subitem.label}}</nuxt-link>
                        </el-menu-item>
                    </el-submenu>
                  </template>
              </el-menu>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    data() {
      return {
        activeIndex: '99',
        showNavbar: true,
        lastScrollPosition: 0,
        menu: Object,
        menuIndex: 1
      };
    },
    created(){
      this.fetchMenuContent()
    },
    mounted () {
      window.addEventListener('scroll', this.onScroll)
    },
    beforeDestroy () {
      window.removeEventListener('scroll', this.onScroll)
    },
    methods: {
      handleSelect(key, keyPath) {
        //alert(key, keyPath);
        this.activeIndex = key;
      },
      handleLogoClicked(){
        this.activeIndex = '99';
      },
      async fetchMenuContent() {
        const menu = await this.$axios.$get('/api/main-menu')
        this.menu = menu
      },
      onScroll () {
        const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop
        if (currentScrollPosition < 0) {
          return
        }
        // Stop executing this function if the difference between
        // current scroll position and last scroll position is less than some offset
        if (Math.abs(currentScrollPosition - this.lastScrollPosition) < 100) {
          return
        }
        this.showNavbar = currentScrollPosition < this.lastScrollPosition
        this.lastScrollPosition = currentScrollPosition
      }
    }
  }
</script>

<style scoped lang="scss">
    .menu-wrapper{
        background-color:rgba(1, 11, 27, 0.8);
        position: fixed;
        width: 100%;
        transform: translate3d(0, 0, 0);
        transition: 0.3s all ease-out;
        z-index: 10;
        &.inner-wrapper, .content-wrapper{
            height: $menu-height;
            @media screen and (max-width: $media-mobile) {
              height: $menu-height-mobile;
            }
        }
        .content-wrapper{
            display: flex;
            align-items: center;
            .logo{
              flex: 1;
              @media screen and (max-width: $media-mobile) {
                img{
                  width: 70px;
                }
              }
            }
        }
    }
    .el-menu{
      @media screen and (max-width: $media-mobile) {
        display: none;
      }
    }
    .el-menu.el-menu--horizontal{
      border: none;
    }
    .el-menu--horizontal>.el-menu-item,.el-menu--horizontal>.el-submenu{
      height: 30px;
      line-height: 30px;
      font-size: 16px;
      font-family: $font-headlines;
      font-weight: 700;
      padding: 0px;
      margin: 0 35px;
      text-transform: uppercase;
      a{
        text-decoration: none;
      }
    }
    .el-submenu__title{
      background-color: green !important;
    }
    .el-menu--horizontal .el-menu-item:not(.is-disabled):focus, .el-menu--horizontal .el-menu-item:not(.is-disabled):hover{
      background-color: transparent !important;
      color: $color-brand !important;
    }
    .el-menu-item * {
      vertical-align: unset;
    }
    .menu-wrapper.navbar--hidden {
      box-shadow: none;
      transform: translate3d(0, -100%, 0);
    }
</style>