<template>
  <div class="app">
    <div class="bg">
      <b-header></b-header>
      <div class="content">

        <category></category>
        <div class="main">
          <nuxt/>
        </div>
        <hot-list></hot-list>
        <calendar></calendar>
      </div>
      <footer></footer>
    </div>
  </div>
</template>
<script>
  import calendar from "../components/calendar/calendar";
    import bHeader from '../components/bHeader/bHeader'
    import category from "../components/category/category";
    import hotList from "../components/hotList/hotList";
    export default {
        components: {
            bHeader,category,calendar,hotList
        },
        data() {
            return {}
        },
        mounted(){
            //document.body.setAttribute('data-theme','default') ;
        },
        methods: {},
        // async asyncData(ctx) {
        //     let {status, data: {code, data: {name, price}}} = await ctx.$axios.post('/getArticleList')
        //     // if(status===200&&code===0&&name){
        //     //     return {
        //     //         cart:[{
        //     //             name,
        //     //             price,
        //     //             count:1
        //     //         }],
        //     //         cartNo:ctx.query.id
        //     //     }
        //     // }
        //     console.log(data)
        // }

    }
</script>
<style lang="scss">
  /*background-image:*/
  /*radial-gradient(white, rgba(255,255,255,.2) 2px, transparent 40px),*/
  /*radial-gradient(white, rgba(255,255,255,.15) 1px, transparent 30px),*/
  /*radial-gradient(white, rgba(255,255,255,.1) 2px, transparent 40px),*/
  /*radial-gradient(rgba(255,255,255,.4), rgba(255,255,255,.1) 2px, transparent 30px);*/
  /*background-size: 550px 550px, 350px 350px, 250px 250px, 150px 150px;*/
  /*background-position: 0 0, 40px 60px, 130px 270px, 70px 100px;*/
  @import '../assets/css/_themeify.scss';
  .app {
    background-blend-mode: multiply;
    background:url('../assets/img/bgcode.jpg') ;
    background-size: 600px 180px ;
    @include themeify {
      //background-color: themed('bg-color-grey');
        background-color: themed('bg-img-color');
    }

    /*@keyframes scles {
      0%{
        background-image:
          radial-gradient(#EB7347, #EB7347 10px, transparent 100px),
          radial-gradient(#FC9D99, #FC9D99 1px, transparent 70px),
          radial-gradient(#AEDD81, #AEDD81 2px, transparent 50px),
          radial-gradient( #00CCFF,  #00CCFF 2px, transparent 60px);
        background-size: 600px 600px, 350px 350px, 500px 500px, 350px 350px;
        background-position: -200px -130px, 1200px 200px, 30px 220px, 70px 100px;
      }
      20%{
        background-image:
          radial-gradient(#EB7347, #EB7347 10px, transparent 100px),
          radial-gradient(#FC9D99, #FC9D99 1px, transparent 70px),
          radial-gradient(#AEDD81, #AEDD81 2px, transparent 52px),
          radial-gradient( #00CCFF,  #00CCFF 2px, transparent 60px);
        background-size: 600px 600px, 350px 350px, 500px 500px, 350px 350px;
        background-position: -200px -135px, 1202px 200px, 30px 220px, 70px 100px;

      }
      40%{
        background-image:
          radial-gradient(#EB7347, #EB7347 10px, transparent 100px),
          radial-gradient(#FC9D99, #FC9D99 1px, transparent 70px),
          radial-gradient(#AEDD81, #AEDD81 2px, transparent 54px),
          radial-gradient( #00CCFF,  #00CCFF 2px, transparent 60px);
        background-size: 600px 600px, 350px 350px, 500px 500px, 350px 350px;
        background-position: -200px -140px, 1204px 200px, 30px 220px, 70px 100px;
      }
      50%{
        background-image:
          radial-gradient(#EB7347, #EB7347 10px, transparent 100px),
          radial-gradient(#FC9D99, #FC9D99 1px, transparent 70px),
          radial-gradient(#AEDD81, #AEDD81 2px, transparent 56px),
          radial-gradient( #00CCFF,  #00CCFF 2px, transparent 60px);
        background-size: 600px 600px, 350px 350px, 500px 500px, 350px 350px;
        background-position: -200px -145px, 1206px 200px, 30px 220px, 70px 100px;
      }
      60%{
        background-image:
          radial-gradient(#EB7347, #EB7347 10px, transparent 100px),
          radial-gradient(#FC9D99, #FC9D99 1px, transparent 70px),
          radial-gradient(#AEDD81, #AEDD81 2px, transparent 54px),
          radial-gradient( #00CCFF,  #00CCFF 2px, transparent 60px);
        background-size: 600px 600px, 350px 350px, 500px 500px, 350px 350px;
        background-position: -200px -140px, 1204px 200px, 30px 220px, 70px 100px;
      }
      80%{
        background-image:
          radial-gradient(#EB7347, #EB7347 10px, transparent 100px),
          radial-gradient(#FC9D99, #FC9D99 1px, transparent 70px),
          radial-gradient(#AEDD81, #AEDD81 2px, transparent 52px),
          radial-gradient( #00CCFF,  #00CCFF 2px, transparent 60px);
        background-size: 600px 600px, 350px 350px, 500px 500px, 350px 350px;
        background-position: -200px -135px, 1202px 200px, 30px 220px, 70px 100px;
      }
      100%{
        background-image:
          radial-gradient(#EB7347, #EB7347 10px, transparent 100px),
          radial-gradient(#FC9D99, #FC9D99 1px, transparent 70px),
          radial-gradient(#AEDD81, #AEDD81 2px, transparent 50px),
          radial-gradient( #00CCFF,  #00CCFF 2px, transparent 60px);
        background-size: 600px 600px, 350px 350px, 500px 500px, 350px 350px;
        background-position: -200px -130px, 1200px 200px, 30px 220px, 70px 100px;
      }
    }*/
  }
  .bg{
    position: absolute;
    width: 100%;
    height: 100%;
    overflow: auto;
    z-index: 10;
    @include themeify {
       //background-color: themed('bg-color-grey');
       background-color: themed('bg-image-op');
    }

  }
  .content{
    margin: auto;
    position: relative;
    width: 1100px;
    display: flex;
    top: 80px;
    .main{
      position: relative;
      left: 180px;
    }
  }
  //animation: scles 10s linear infinite;
  .app:after {
    content: "";
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    /*@include themeify {
      //background-color: themed('bg-color-grey');
      background-color: themed('bg-image-op');
    }*/
    background: inherit;
    filter: blur(3px);
    //position: relative;
    z-index: 2;
  }
  ::-webkit-scrollbar {
    width: 5px;
    height: 10px;
    background: rgba(0,0,0,0.1);
  }
  ::-webkit-scrollbar-thumb {
    border-radius: 0;
    background-color: rgba(95,95,95,.4);

    transition: .1s;
  }
</style>
