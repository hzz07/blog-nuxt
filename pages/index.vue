<template>
  <div class="container">
    <banner></banner>
    <article-list></article-list>
  </div>
</template>

<script>
    import banner from '../components/banner/banner'
    import articleList from "../components/articleList/articleList";
    export default {
        components: {
          banner,articleList
        },
        data() {
          return {
            title: '起航'
          }
        },
        head () {
          return {
            title: this.title,
            meta: [
              { hid: 'qihang', name: 'description', content: '起航' }
            ]
          }
        },
        methods: {
            send :async function(){
                let {data:{data},data:{code}} = await this.$axios.post('/getArticleList')
                console.log(data,{code})
            }
        },
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

<style lang="scss" scoped>
  @import '@/assets/css/_themeify.scss';
  .container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    /*justify-content: center;*/
    /*align-items: center;*/
    /*text-align: center;*/
    @include themeify {
      //background-color: themed('bg-color-white');
      width: 650px;
    }
  }
</style>
