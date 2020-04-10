<template>
    <div class="box">
        <div class="swiper swiperBox" v-swiper:swiper="swiperOption" @mouseenter="stopSwiper"
             @mouseleave="startSwiper">
            <div class="swiper-wrapper">
                <div class="swiper-slide" v-for="(banner,i) in banners" :key="i">
                    <nuxt-link to="#">
                        <img :src="banner.img">
                        <div class="text-info">
                            <h2>{{banner.text}}</h2>
                        </div>
                    </nuxt-link>

                </div>
            </div>
            <div class="swiper-pagination" slot="pagination"></div>


        </div>
        <div class="slineBox">
            <div class="sline swiperBox" ref="swiperline" v-swiper:LineSwiper="swiperOptionLines">
                <div class="timeIcon" ref="timeIcon">
                    <img src="../../assets/img/clock.png" alt="">
                </div>
                <div class="swiper-wrapper">
                    <div class="swiper-slide" v-for="(article,i) in updateArticle" :key="i">
                        <h2>{{article.text}}</h2>
                        <p>{{article.time}}</p>
                    </div>
                </div>
            </div>
            <div class="swpBtn">
                <div class="swiperPrev">
                    <a href="javascript:;">
                        <i class="iconfont">&#xe605;</i>
                    </a>
                </div>
                <div class="swiperNext">
                    <a href="javascript:;">
                        <i class="iconfont">&#xe604;</i>
                    </a>

                </div>
            </div>
        </div>

        <svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg"
             xmlns:xlink="http://www.w3.org/1999/xlink"
             width="0" height="0" viewBox="0 0 1366 768" xml:space="preserve">
          <!-- Gaussian blur filtter progression to animate -->
          <defs>
            <filter id="blur0">
              <feGaussianBlur in="SourceGraphic" stdDeviation="12,0"></feGaussianBlur>
            </filter>
              <filter id="blur1">
              <feGaussianBlur in="SourceGraphic" stdDeviation="6,0"></feGaussianBlur>
            </filter>
              <filter id="blur2">
              <feGaussianBlur in="SourceGraphic" stdDeviation="0,10"></feGaussianBlur>
            </filter>
              <filter id="blur3">
              <feGaussianBlur in="SourceGraphic" stdDeviation="0,4"></feGaussianBlur>
            </filter>
              <!--              <filter id="blur4">-->
              <!--              <feGaussianBlur in="SourceGraphic" stdDeviation="12 0"></feGaussianBlur>-->
              <!--            </filter>-->
              <!--              <filter id="blur5">-->
              <!--              <feGaussianBlur in="SourceGraphic" stdDeviation="12 0"></feGaussianBlur>-->
              <!--            </filter>-->
          </defs>
        </svg>
    </div>
</template>

<script>
    export default {
        name: "banner",
        data() {
            return {
                banners: [
                    {
                        img: require('../../assets/img/banner1.jpg'),
                        text: 'javascript指南'
                    },
                    {
                        img: require('../../assets/img/banner2.jpg'),
                        text: 'react源码解析'
                    },
                    {
                        img: require('../../assets/img/banner3.jpg'),
                        text: 'vue性能优化和监听器原理'
                    },
                    {
                        img: require('../../assets/img/banner4.jpg'),
                        text: '生活和自由'
                    },
                ],
                updateArticle: [
                    {
                        text: '无为而治',
                        time: '20天以前~'
                    },
                    {
                        text: '空想患者',
                        time: '5周以前~'
                    },
                    {
                        text: '一切都需要自己想要什么才能去做',
                        time: '2小时以前~'
                    },
                    {
                        text: '思想匮乏，精神空虚',
                        time: '刚刚~'
                    },
                ],
                // 所有配置均为可选（同Swiper配置）
                swiperOption: {
                    loop: true,
                    speed: 500,
                    // notNextTick是一个组件自有属性，如果notNextTick设置为true，组件则不会通过NextTick来实例化swiper，也就意味着你可以在第一时间获取到swiper对象，假如你需要刚加载遍使用获取swiper对象来做什么事，那么这个属性一定要是true
                    notNextTick: false,
                    slidesPerView: 'auto',
                    centeredSlides: true,
                    pagination: {
                        el: '.swiper-pagination',
                        clickable: true
                    },
                    // navigation: {
                    //     nextEl: '.swiper-button-next',
                    //     prevEl: '.swiper-button-prev',
                    // },
                    on: {
                        transitionStart() {
                            //console.log(this)
                            this.$wrapperEl[0].classList.add('do-transition');
                        },
                        transitionEnd() {
                            this.$wrapperEl[0].classList.remove('do-transition')
                        },
                        slideChange() {

                        },

                    },
                    autoplay: {
                        delay: 3500,
                        disableOnInteraction: true,
                    },
                    autoplayDisableOnInteraction: false,
                    effect: 'fade',
                    mousewheel: true,
                    preloadImages: false,
                    lazy: false
                },
                swiperOptionLines: {
                    loop: true,
                    speed: 500,
                    // notNextTick是一个组件自有属性，如果notNextTick设置为true，组件则不会通过NextTick来实例化swiper，也就意味着你可以在第一时间获取到swiper对象，假如你需要刚加载遍使用获取swiper对象来做什么事，那么这个属性一定要是true
                    notNextTick: false,
                    slidesPerView: 'auto',
                    centeredSlides: true,
                    direction: 'vertical',
                    pagination: {
                        el: '.swiper-paginationLines',
                        clickable: true
                    },
                    navigation: {
                        nextEl: '.swiperPrev',
                        prevEl: '.swiperNext',
                    },
                    on: {
                        transitionStart() {
                            this.$wrapperEl[0].classList.add('text-transition');
                            let index = this.activeIndex;
                            this.$el[0].firstElementChild.children[0].style.transform = 'rotate(' + index * 90 + 'deg)';
                        },
                        transitionEnd() {
                            this.$wrapperEl[0].classList.remove('text-transition');

                        },
                        slideChange() {

                        },

                    },
                    autoplay: {
                        delay: 3500,
                        disableOnInteraction: false,
                    },
                    autoplayDisableOnInteraction: true,
                    effect: '',
                    mousewheel: true,
                    preloadImages: false,
                    lazy: false
                }
            }
        },
        watched: {},
        swiper() {
            return this.$refs.swiperline.$swiper
        },
        methods: {
            stopSwiper() {
                this.swiper.autoplay.stop()
            },
            startSwiper() {
                this.swiper.autoplay.start()
            },
            transitionStart() {
                this.$wrapperEl[0].classList.add('text-transition');

            },
        },
        mounted() {


        }
    }
</script>

<style scoped lang="scss">
    @import '@/assets/css/_themeify.scss';

    .box {
        position: relative;
        width: 100%;

        .swiper-slide-active[data-swiper-slide-index='0'] {
            img {
                animation-duration: 0.5s;
                animation-timing-function: linear;
                animation-fill-mode: forwards;
                -webkit-animation-duration: 3.8s;
                -webkit-animation-timing-function: linear;
                -webkit-animation-fill-mode: forwards;
                -webkit-animation-name: leftUp;
                animation-name: leftUp;
                @-webkit-keyframes leftUp {
                    0% {
                        transform: scale(1.1, 1.1) translate(4.545%, 4.545%);
                    }
                    100% {
                        transform: scale(1.1, 1.1) translate(-4.545%, -4.545%);
                    }
                }
                @keyframes leftUp {
                    0% {
                        transform: scale(1.1, 1.1) translate(4.545%, 4.545%);
                    }
                    100% {
                        transform: scale(1.1, 1.1) translate(-4.545%, -4.545%);
                    }
                }
            }
        }

        .swiper-slide-active[data-swiper-slide-index='1'] {
            img {
                animation-duration: 0.5s;
                animation-timing-function: linear;
                animation-fill-mode: forwards;
                -webkit-animation-duration: 3.8s;
                -webkit-animation-timing-function: linear;
                -webkit-animation-fill-mode: forwards;
                -webkit-animation-name: moveRight;
                animation-name: moveRight;
                @-webkit-keyframes moveRight {
                    0% {
                        transform: scale(1.1, 1.1) translate(-4.545%, 0);
                    }
                    100% {
                        transform: scale(1.1, 1.1) translate(4.545%, 0);
                    }
                }
                @keyframes moveRight {
                    0% {
                        transform: scale(1.1, 1.1) translate(-4.545%, 0);
                    }
                    100% {
                        transform: scale(1.1, 1.1) translate(4.545%, 0);
                    }
                }
            }
        }

        .swiper-slide-active[data-swiper-slide-index='2'] {
            img {
                animation-duration: 0.5s;
                animation-timing-function: linear;
                animation-fill-mode: forwards;
                -webkit-animation-duration: 3.8s;
                -webkit-animation-timing-function: linear;
                -webkit-animation-fill-mode: forwards;
                -webkit-animation-name: moveDown;
                animation-name: moveDown;
                @-webkit-keyframes moveDown {
                    0% {
                        transform: scale(1.1, 1.1) translate(0, -4.545%);
                    }
                    100% {
                        transform: scale(1.1, 1.1) translate(0, 4.545%);
                    }
                }
                @keyframes moveDown {
                    0% {
                        transform: scale(1.1, 1.1) translate(0, -4.545%);
                    }
                    100% {
                        transform: scale(1.1, 1.1) translate(0, 4.545%);
                    }
                }
            }
        }

        .swiper-slide-active[data-swiper-slide-index='3'] {
            img {
                animation-duration: 0.5s;
                animation-timing-function: linear;
                animation-fill-mode: forwards;
                -webkit-animation-duration: 3.8s;
                -webkit-animation-timing-function: linear;
                -webkit-animation-fill-mode: forwards;
                -webkit-animation-name: centerBig;
                animation-name: centerBig;
                @-webkit-keyframes centerBig {
                    100% {
                        transform: scale(1.1, 1.1);
                    }
                }
                @keyframes centerBig {
                    100% {
                        transform: scale(1.1, 1.1);
                    }
                }
            }
        }

        .swiper-slide-active[data-swiper-slide-index='4'] {
            img {
                animation-duration: 0.5s;
                animation-timing-function: linear;
                animation-fill-mode: forwards;
                -webkit-animation-duration: 3.8s;
                -webkit-animation-timing-function: linear;
                -webkit-animation-fill-mode: forwards;
                -webkit-animation-name: rightDownBig;
                animation-name: rightDownBig;
                @-webkit-keyframes rightDownBig {
                    100% {
                        transform: scale(1.1, 1.1) translate(4%, 4%);
                    }
                }
                @keyframes rightDownBig {
                    100% {
                        transform: scale(1.1, 1.1) translate(4%, 4%);
                    }
                }
            }
        }

        .swiper {
            @include themeify {
                height: themed(bannerHeight);
            }
            overflow: hidden;

            .text-info {
                position: absolute;
                min-width: 0%;
                padding: 0 30px;
                z-index: 99;
                height: 30px;
                @include themeify {
                    background-image: linear-gradient(to right, rgba(255, 255, 255, 0.7) 0%, rgba(0, 0, 0, 0) 100%);
                }
                top: 0;
                transition: 0.3s;

                h2 {
                    transition: 0.3s;
                    font-family: cursive;
                    @include themeify {
                        color: themed(text-color-white);
                        line-height: 30px;
                    }
                }
            }
        }

        .slineBox {
            position: relative;

            .sline {
                margin-top: 10px;
                @include themeify {
                    height: themed(lineHeight);
                }
                overflow: hidden;
                position: relative;
                display: flex;
                align-items: center;
                width: 100%;
                background: linear-gradient(to right, rgba(0, 0, 0, 0.4) 0, rgba(225, 225, 225, 0.5) 55%, rgba(225, 225, 225, 1) 100%);

                .timeIcon {
                    padding-left: 20px;

                    img {
                        width: 20px;
                        height: 20px;
                        transition: 0.5s;
                    }
                }

                .swiper-slide {
                    display: flex;

                    h2 {
                        @include themeify {
                            line-height: themed(lineHeight);
                        }
                        padding-left: 30px;
                        width: 65%;
                        @include themeify {
                            font-size: themed(font-size-default-s);
                            color: themed(text-color-white);
                        }
                    }

                    p {
                        @include themeify {
                            line-height: themed(lineHeight);
                        }
                        @include themeify {
                            font-size: themed(font-size-default-s);
                            color: themed(text-color-default-q);
                            z-index: 999;
                        }
                    }
                }

            }

            .sline:after {
                content: '';
                display: block;
                width: 10px;

            }

            .swpBtn {
                z-index: 99;
                position: absolute;
                right: 0;
                top: 0;
                width: 30%;
                @include themeify {
                    height: themed(lineHeight);
                }
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-items: center;

                div {
                    margin-left: 70%;

                    a {
                        display: block;
                        width: 30px;
                        text-decoration: none;
                        text-align: center;
                        @include themeify {
                            color: themed(text-color-black);
                        }

                        i {
                            display: block;
                            transform: scale(1, 0.5);
                            @include themeify {
                                color: themed(text-color-placeholder);
                            }
                        }
                    }

                    a:hover {
                        i {
                            @include themeify {
                                color: themed(text-color-black);
                            }
                        }
                    }
                }
            }
        }

        img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            //transition: 0.3s;
        }

        a {
            .text-info:hover {
                transition: 0.3s;

                h2 {
                    transition: 0.3s;
                    color: rgba(255, 255, 255, 1) !important;
                }

                background-image: linear-gradient(to right, rgba(73, 90, 255, 1) 0%, rgba(255, 255, 255, 0) 100%) !important
            }
        }

        .swiper-pagination {
            left: 40%;
        }
    }

    .do-transition {
        filter: url(#blur0);
    }

    .text-transition {
        filter: url(#blur3);
    }

    @keyframes moves {
        0% {
            transform-origin: top left;
            transform: scale(1);
        }
        100% {
            transform-origin: top left;
            transform: scale(1.1);
        }
    }
</style>
