<template>
  <div class="box">
    <header>
      <div class="left">
        <a href="javascript:;">
          <svg t="1584326271712" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
               p-id="1374" xmlns:xlink="http://www.w3.org/1999/xlink" width="200" height="200">
            <defs>
              <style type="text/css"></style>
            </defs>
            <path
              d="M824.888889 630.992593l-122.026667-50.346667a28.444444 28.444444 0 1 0-21.143703 53.57037l60.112592 24.367408-60.112592 27.591111a28.444444 28.444444 0 0 0-14.601482 37.357037A28.918519 28.918519 0 0 0 693.096296 739.555556a15.454815 15.454815 0 0 0 11.377778-3.223704l120.414815-54.992593a28.918519 28.918519 0 0 0 16.213333-25.979259A25.694815 25.694815 0 0 0 824.888889 630.992593zM548.598519 517.30963a28.444444 28.444444 0 0 0-35.745186 17.825185l-61.629629 188.397037a28.444444 28.444444 0 0 0 17.825185 35.745185 17.540741 17.540741 0 0 0 8.154074 1.611852 31.668148 31.668148 0 0 0 27.591111-19.531852l61.724445-188.302222a28.444444 28.444444 0 0 0-17.92-35.745185zM358.684444 597.333333a30.151111 30.151111 0 0 0-37.357037-16.213333L199.111111 630.992593a30.435556 30.435556 0 0 0-17.825185 25.979259A28.444444 28.444444 0 0 0 197.973333 682.666667l120.130371 55.182222a30.056296 30.056296 0 0 0 11.377777 3.223704 28.918519 28.918519 0 0 0 25.97926-16.213334 28.444444 28.444444 0 0 0-14.601482-37.357037l-60.112592-27.591111 60.112592-24.367407c16.213333-7.774815 24.367407-24.082963 17.825185-38.210371z"
              fill="#5176e8" p-id="1375"></path>
            <path
              d="M853.333333 170.666667a56.888889 56.888889 0 0 1 56.888889 56.888889v568.888888a56.888889 56.888889 0 0 1-56.888889 56.888889H170.666667a56.888889 56.888889 0 0 1-56.888889-56.888889V227.555556a56.888889 56.888889 0 0 1 56.888889-56.888889h682.666666m0-56.888889H170.666667A113.777778 113.777778 0 0 0 56.888889 227.555556v568.888888a113.777778 113.777778 0 0 0 113.777778 113.777778h682.666666a113.777778 113.777778 0 0 0 113.777778-113.777778V227.555556a113.777778 113.777778 0 0 0-113.777778-113.777778z"
              fill="#5176e8" p-id="1376"></path>
            <path d="M967.111111 365.321481H56.888889v56.888889h910.222222v-56.888889z" fill="#5176e8" p-id="1377"></path>
            <path class="d d1"
              d="M224.995556 273.540741m-42.666667 0a42.666667 42.666667 0 1 0 85.333333 0 42.666667 42.666667 0 1 0-85.333333 0Z"
              fill="#5176e8" p-id="1378"></path>
            <path class="d d2"
              d="M357.451852 273.540741m-42.666667 0a42.666667 42.666667 0 1 0 85.333334 0 42.666667 42.666667 0 1 0-85.333334 0Z"
              fill="#5176e8" p-id="1379"></path>
            <path class="d d3"
              d="M489.908148 273.540741m-42.666667 0a42.666667 42.666667 0 1 0 85.333334 0 42.666667 42.666667 0 1 0-85.333334 0Z"
              fill="#5176e8" p-id="1380"></path>
          </svg>
        </a>
      </div>
      <div class="right">
        <a href="javascript:;">RESOLVE</a>

      </div>
      <div class="reMind">
        不要死，也不要孤独的活着
      </div>
      <search></search>
    </header>

  </div>
</template>

<script>
  import search from "../search/search";
    export default {
        name: "bHeader",
        data(){
            return{

            }
        },
        components:{
            search
        }
    }
</script>

<style scoped lang="scss">
  @import '@/assets/css/_themeify.scss';
  .box {
    display: flex;
    justify-content: center;
    //position: relative;
    height: 60px;
    width: 100%;
    z-index: 10;
    position: fixed;
    @include themeify {
      background-color: themed('bg-color-white-op');
    }
    box-shadow:0 0 100px 1px rgba(0,0,0,0.1);
    header {
      display: flex;
      align-items: center;
      width: 1100px;
      position: relative;

      .left{
        svg{
          width: 60px ;
          height: 40px;
          .d{
            opacity: 0;
          }
          .d1{
            animation-delay: 1s;
            animation: ds1 2s  both infinite;
          }
          .d2{
            animation-delay: 1s;
            animation: ds2 2s  both infinite;
          }
          .d3{
            animation-delay: 1s;
            animation: ds3 2s  both infinite;
          }

        }
        .icon{
          animation: scals 2s  both infinite;
          animation-delay: 1s;
        }
      }
      .right{
        font-family: -webkit-pictograph;
        font-size: 36px;
        font-weight: 600;
        color: #7f828b;
        position: relative;
        display: flex;
        transition: 0.6s;
        margin-left: 22px;
        a{
          background-image: linear-gradient(to bottom, white 0%,cornflowerblue 15%,cornflowerblue 75%,white 100%);
          text-decoration: none;
          -webkit-background-clip: text;
          color: transparent;
          -webkit-text-fill-color: transparent;
          text-fill-color: transparent;
        }
        p{
          margin-left: 60px;
        }
      }
      .reMind{
        margin-left: 60px;
        font-family: cursive;
        @include themeify {
          color: themed(text-color-header-i);
        }
      }
      .right:hover{
        transition: 0.6s;
        transform-origin: center;
        transform: scale3d(1.1,1.1,1.1);
        a{
          @include themeify {
            color: themed(text-color-header-i);
          }
        }

      }
      .right:after{
        display: block;
        position: absolute;
        content: '';
        width: 8px;
        height: 40px;
        background-color: white;
        filter:blur(3px);
        transform: rotate(45deg);
        left: -13%;
        animation:show 5s linear infinite;
      }
    }
    @keyframes scals {
      0% {
        transform: scale(1);
        transform: scale(1)
      }

      70%,73%{
        transform: scale(0.9) rotate(-3deg);
        transform: scale(0.9) rotate(-3deg)
      }

      77%,83%,90%,97%  {
        transform: scale(1.1) rotate(3deg);
        transform: scale(1.1) rotate(3deg)
      }

      80%,87%,93%{
        transform: scale(1.1) rotate(-3deg);
        transform: scale(1.1) rotate(-3deg)
      }

      100% {
        transform: scale(1) rotate(0);
        transform: scale(1) rotate(0)
      }
    }
    @keyframes ds1 {
      0%{
        //transform: scale(1.5);
        opacity: 0;
      }
      33.3%{
        opacity: 1;
      }
      100%{
        opacity: 1;
      }
    }
    @keyframes ds2 {
      0%{
        opacity: 0;
      }
      33.3%{
        opacity: 0;
      }
      66.6%{
        opacity: 1;
      }
      100%{
        opacity: 1;
      }
    }
    @keyframes ds3 {
      0%{
        opacity: 0;
      }
      66.6%{
        opacity: 0;
      }
      100%{
        opacity: 1;
      }
    }
    @keyframes show {
      0%{
        left: -13%;
      }
      50%{
        left: -13%;
      }
      to{
        left: 110%;
      }
    }
  }
</style>
