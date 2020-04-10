<template>
     <div class="category">

               <ul>
                    <li v-for="(item,key) in list" :key="key">
                         <a href="javascript:;">
              <span v-for="(items,keys) in item" :key="keys">
                <span class="out" :style="{transitionDelay:0.05*randomNum(item)+'s'}">{{items}}</span>
                <span class="in" :style="{transitionDelay:0.05*randomNum(item)+'s'}">{{items}}</span>
              </span>
                         </a>
                    </li>
               </ul>

     </div>
</template>

<script>
    export default {
        name: "category",
         data(){
              return{
                   list:[
                        '汇总',
                        'js',
                        'css',
                        'react',
                        '随笔'
                   ]
              }
         },
         methods:{
              randomNum(arr){
                   return Math.floor(Math.random()*arr.length)
              }
         }
    }
</script>

<style scoped lang="scss">
  @import '@/assets/css/_themeify.scss';
  .category{
       overflow: hidden;
       width: 180px;
       /*@include themeify {
            background-color: themed('bg-color-white');
            width: 200px;
       }*/
       display: flex;
       align-items: center;
       justify-content: center;
       position: fixed;
       ul{
            position: relative;
            color: black;
            /*display: flex;*/
            width: auto;
            li{
                 font-family: Lato, sans-serif;
                 line-height: 40px;
                 list-style-type: none;
                 flex: 1;
                 flex-shrink: 1;
                 display: flex;
                 text-align: center;
                 position: relative;
                 justify-content: center;
                 align-items: center;
                 flex-direction: column;
                min-width:150px ;
                 a{
                     font-family: 微软雅黑;

                     @include themeify {
                         color: themed(text-color-default-q);
                     }
                      text-decoration: none;
                      span{
                           position: relative;
                           overflow: hidden;
                           transition: 0.3s cubic-bezier(0.165, 0.84, 0.44, 1);
                           @include themeify {
                                font-size: themed('font-size-default');
                           }
                           .out {
                                display: inline-flex;
                           }

                           .in {
                                position: absolute;
                                left: 0;
                                opacity: 0;
                                transform: translateX(100%);
                           }
                      }
                 }

            }
            /*li:after{
                 content: '';
                 display: block;
                 position: relative;
                 height: 3px;
                 left: 0;
                 right: 0;
                 width: 0%;
                 background-color: #495aff;
                 bottom: 0;
                 transition: 0.3s cubic-bezier(0.165, 0.84, 0.44, 1);
            }*/
            li:hover{

                @include themeify{
                    background-color: themed(bg-color-white);
                }
                a{


                    span{
                        @include themeify{
                            color: themed(text-color-header-i);
                        }
                        font-weight: 600;
                        .out {
                            opacity: 0;
                            transform: translateX(-100%);
                        }

                        .in {
                            opacity: 1;
                            transform: translateX(0);
                        }
                    }
                }
                /*&:after{*/
                /*    width: 100%;*/
                /*}*/

            }


       }

  }
</style>
