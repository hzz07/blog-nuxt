<template>
    <div :class='["search",showS?"show":""]' @click="show">
        <a href="javascript:;"><i class="iconfont">&#xe61e;</i></a>
        <input type="text" placeholder="搜索..." v-model="searchValue">
    </div>
</template>

<script>
    export default {
        name: "search",
        data(){
          return{
            showS:false,
            searchValue:''
          }
        },
      methods:{
        show(){
          this.showS = true
        }
      }

    }
</script>

<style scoped lang="scss">
    @import '@/assets/css/_themeify.scss';

    .search {
        padding: 3px 20px 3px 3px;

        border-radius: 25px;
        position: absolute;
        right: 0;
        display: flex;
        justify-content: center;
        align-items: center;

        a {
            text-decoration: none;
            i {
              transition: 0.2s;
                @include themeify {
                    background-color: themed('bg-color-text-bg');
                }
                flex-shrink: 0;
                display: block;
                width: 40px;
                height: 40px;
                line-height: 40px;
                border-radius: 50%;
                color: black;
                text-align: center;
                align-items: center;
            }
        }

        input {
            height: 0px;
            width: 0px;
            opacity: 0;
            border: none;
            border-bottom: 1px solid rgba(0, 0, 0, 0.1);
            background-color: transparent;
            transition: 0.4s;
        }
        i:hover {
          transition: 0.2s;
            @include themeify {
                background-color: themed('bg-search-op');
            }
          color: white;
        }
    }

    .show {
      @include themeify {
        background-color: themed('bg-color-text-bg');
      }
      input {
        height: 20px;
        width: 150px;
        opacity: 1;
      }
    }
</style>
