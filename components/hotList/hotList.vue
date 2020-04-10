<template>
    <div class="hotbox">
        <h1><i class="iconfont">&#xe66c;</i>当前热门文章</h1>
        <ul>
            <a href="javascript:;" v-for="(item,index) in list" :key="index">
                <li> <span>{{index+1}}</span><p>{{item}}</p> </li>
            </a>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "hotList",
        data(){
            return{
                list:['外观设置中，无法改变代码的字体的问题 ',

                       ' 为什么打开后画面显示不正常的问题 ',

                        'iOS 的 SDK 里有 base64 的库与 cocos 引擎冲突的问题 ',

                        '头像无法更换的问题 ']
            }
        }
    }
</script>

<style scoped lang="scss">
    @import '@/assets/css/_themeify.scss';

    .hotbox {
        width: 240px;
        position: fixed;
        right: 270px;
        //padding: 10px 10px;
        @include themeify {
            background-color: themed(bg-color-white);
        }

        h1 {
            @include themeify {
                font-size: themed(font-size-default);
                color: themed(text-color-default);
                background-color: themed(bg-color-text-bg);
                i {
                    color: red;
                    padding: 0 10px;
                }
                padding: 10px 0;
            }
        }
        ul{
            display: flex;
            flex-direction: column;
            a{
                li{
                    line-height: 20px;

                    display: flex;
                    span{
                        flex-shrink: 0;
                        display: block;
                        width: 30px;
                        line-height: 30px;
                        text-align: center;
                        @include themeify {
                            font-size: themed(font-size-default-s);
                            color: themed(text-color-default-q);
                        }
                    }
                    p{
                        flex: 1;
                        overflow: hidden;
                        text-overflow: ellipsis;
                        white-space: nowrap;
                        line-height: 30px;
                        padding-left: 5px;
                        @include themeify {
                            font-size: themed(font-size-default-s);
                            color: themed(text-color-default);
                        }
                    }
                }
            }
            a:hover{
                @include themeify {
                    background-color: themed(text-color-disabled);
                    transition: 0.1s ;
                }
            }
            a:nth-child(1){
                span{
                    @include themeify {
                        color: themed(first-color);
                    }
                }
            }
            a:nth-child(2){
                span{
                    @include themeify {
                        color: themed(second-color);
                    }
                }
            }
            a:nth-child(3){
                span{
                    @include themeify {
                        color: themed(third-color);
                    }
                }
            }

        }

    }
</style>
