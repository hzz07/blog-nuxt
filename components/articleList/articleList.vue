<template>
    <div class="articleList">
        <ul>
            <li v-for="(list,index) in articleList"
                :class="['category'+list.origin, 'itemBox']"
                :key="index">
                <div class="articleLeft">
                    <img :src="list.img_url" :alt="list.desc">
                </div>
                <div class="articleRight">
                    <div>
                        <a href="javascript:;">
                            <h3>
                                {{list.title}}
                            </h3>
                        </a>

                        <p>{{list.desc}}</p>
                    </div>


                    <ul>
                        <li><i class="iconfont">&#xe661;
                        </i>{{list.other.views}}
                        </li>
                        <li><i class="iconfont">&#xe644;
                        </i>{{list.other.likes}}
                        </li>
                        <li><i class="iconfont">&#xe665;
                        </i>{{list.other.comments}}
                        </li>
                        <li><i class="iconfont">&#xe64d;
                        </i>{{list.create_time.split('T')[0]}}
                        </li>
                    </ul>

                </div>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "articleList",
        data() {
            return {
                articleList: [
                    {
                        "other": {
                            "views": 9,
                            "likes": 0,
                            "comments": 0
                        },
                        "desc": "react知识总结",
                        "img_url": "http://ww1.sinaimg.cn/large/007UgRf1gy1gcisbqa9xxg30gs08cjrd.jpg",
                        "tags": [],
                        "comments": [],
                        "category": [
                            {
                                "_id": "5e605b3840d36a4678102d6a",
                                "name": "react"
                            }
                        ],
                        "_id": "5e6056eec3802f2e280f163b",
                        "title": "React 的Component 和 PureComponent",
                        "create_time": "2020-03-05T01:33:34.206Z",
                        "origin": '0'
                    },
                    {
                        "other": {
                            "views": 18,
                            "likes": 0,
                            "comments": 0
                        },
                        "desc": "坚持本心，磨炼意志",
                        "img_url": "http://ww1.sinaimg.cn/large/007UgRf1gy1gb2s67jrffj31hc0u0wmu.jpg",
                        "tags": [],
                        "comments": [],
                        "category": [
                            {
                                "_id": "5e5f6f4eb179e306b4427551",
                                "name": "javaScript"
                            }
                        ],
                        "_id": "5e27f1fdf0edef1654067c41",
                        "title": "这是2020年的第3篇文章",
                        "create_time": "2020-01-22T06:55:57.581Z",
                        "origin": '1'
                    },
                    {
                        "other": {
                            "views": 3,
                            "likes": 0,
                            "comments": 0
                        },
                        "desc": "人需有自知",
                        "img_url": "http://ww1.sinaimg.cn/large/007UgRf1gy1gb2s67jrffj31hc0u0wmu.jpg",
                        "tags": [],
                        "comments": [],
                        "category": [
                            {
                                "_id": "5e5f6f4eb179e306b4427551",
                                "name": "javaScript"
                            }
                        ],
                        "_id": "5e26c699833a733fb8c123ed",
                        "title": "这是2020年的第2篇文章",
                        "create_time": "2020-01-21T09:38:33.892Z",
                        "origin": '2'
                    },
                    {
                        "other": {
                            "views": 1,
                            "likes": 0,
                            "comments": 1
                        },
                        "desc": "坚持本心，磨炼意志",
                        "img_url": "http://ww1.sinaimg.cn/large/007UgRf1gy1gb2s67jrffj31hc0u0wmu.jpg",
                        "tags": [],
                        "comments": [
                            {
                                "_id": "5e79b92d008a5b2f547ba101",
                                "article_id": "5e2691b4c3ce6327781dd86b"
                            }
                        ],
                        "category": [],
                        "_id": "5e2691b4c3ce6327781dd86b",
                        "title": "这是2020年的第一篇文章",
                        "create_time": "2020-01-21T05:52:52.461Z",
                        "origin": '1'
                    }
                ]
            }
        },
        methods: {}
    }
</script>

<style scoped lang="scss">
    @import '@/assets/css/_themeify.scss';

    .articleList {
        ul {
            width: 100%;

            .itemBox {
                position: relative;
                margin-top: 10px;
                padding: 15px;
                display: flex;
                overflow: hidden;
                @include themeify {
                    background-color: themed(bg-color-white);
                }

                .articleLeft {
                    width: 150px;
                    height: 90px;
                    position: relative;

                    img {
                        width: 100%;
                        height: 100%;
                        object-fit: cover;
                    }
                }

                .articleRight {
                    flex: 1;
                    display: flex;
                    flex-direction: column;
                    justify-content: space-between;
                    padding: 0 15px;

                    div {
                        a {
                            h3 {
                                font-family: 黑体;
                                @include themeify {
                                    color: themed(text-color-default);
                                }
                            }
                        }

                        p {

                            line-height: 30px;
                            @include themeify {
                                color: themed(text-color-default);
                                font-size: themed(font-size-sm);
                            }
                        }
                    }

                    ul {

                        display: flex;

                        li {
                            flex: 1;
                            font-size: 12px;
                            @include themeify {
                                color: themed(text-color-default-q);
                            }

                            i {
                                font-size: 13px;
                            }
                        }
                    }
                }

            }

            .itemBox:hover {
                transition: 0.3s;
                @include themeify {
                    background-color: themed(bg-hover);
                }
            }

            .itemBox:first-child {
                margin-top: 0;
            }

            .category0:hover {
                transition: 0.3s;
                &:after {
                    content: '原创';
                    top: 0;
                    right: 0;
                    width: 70px;
                    height: 50px;
                    background-color: #13CE66;
                    color: white;
                    position: absolute;
                    justify-content: center;
                    display: flex;
                    line-height: 80px;
                    font-size: 12px;
                    transform: rotate(45deg) translate(10%, -80%);
                }
            }

            .category1:hover {
                &:after {
                    content: '转载';
                    top: 0;
                    right: 0;
                    width: 70px;
                    height: 50px;
                    background-color: orange;
                    color: white;
                    position: absolute;
                    justify-content: center;
                    display: flex;
                    line-height: 80px;
                    font-size: 12px;
                    transform: rotate(45deg) translate(10%, -80%);
                }
            }

            .category2:hover {
                &:after {
                    content: '混合';
                    top: 0;
                    right: 0;
                    width: 70px;
                    height: 50px;
                    background-color: rosybrown;
                    color: white;
                    position: absolute;
                    justify-content: center;
                    display: flex;
                    line-height: 80px;
                    font-size: 12px;
                    transform: rotate(45deg) translate(10%, -80%);
                }
            }

        }
    }
</style>
