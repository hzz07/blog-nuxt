<template>
    <div class="calendar">
        <div class="calendarBox">
            <header>
                <a href="javascript:;" @click="prev"><i class="iconfont ">&#xe600;</i></a>
                {{currentYear}}年 {{currentMonth}}月 {{currentDay}}日
                <a href="javascript:;" @click="next"><i class="iconfont">&#xe601;</i></a>
            </header>
            <div class="weekHead">
                <ul>
                    <li>日</li>
                    <li>一</li>
                    <li>二</li>
                    <li>三</li>
                    <li>四</li>
                    <li>五</li>
                    <li>六</li>
                </ul>
            </div >
            <div class="days">
                <ul >
                    <li v-for="(item,index) in days"
                        :key="index"
                        :class="[
                            (item.getMonth()+1)== currentMonth&&item.getDate()==currentDay ?'today':'',
                            (item.getMonth()+1)!= currentMonth ? 'otherDay':''
                        ]"
                        @click="chooseDay(item)"
                    ><a href="javascript:;">{{item.getDate()}} </a></li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "calendar",
        data(){
            return{
                days:[],
                currentYear:'',
                currentMonth:'',
                currentDay:'',
                firstWeek:''
            }
        },
        created() {
            this.initDays();

        },
        methods:{
            chooseDay(day){
                if(day.getMonth()+1!=this.currentMonth){
                    //console.log(day.getDate())
                    this.getDays(day.getFullYear(), day.getMonth() + 1, day.getDate());
                }else{
                    this.currentYear = day.getFullYear();
                    this.currentMonth =  day.getMonth()+1<10?'0'+parseInt(day.getMonth()+1):day.getMonth()+1;
                    this.currentDay =  day.getDate()<10?'0'+parseInt(day.getDate()):day.getDate();
                }
            },
            initDays(){
                this.getDays()
                /*console.log(this.currentYear,this.currentMonth,this.currentDay)*/
            },
            getDays(y,m,d){
                let date;
                if(y,m){
                    this.currentYear = y;
                    this.currentMonth =  m;
                    if(d){
                        this.currentDay =  d;
                    }
                }else{
                    this.currentYear = this.format('y');
                    this.currentMonth =  this.format('m');
                    this.currentDay =  this.format('d');

                }
                date=new Date(this.currentYear,this.currentMonth-1,1);
                this.firstWeek = date.getDay();
                this.days.length=0;
                //console.log(this.firstWeek ,date.getMonth(),date.getDate())
                for(let i = this.firstWeek;i>0;i--){
                    date=new Date(this.currentYear,this.currentMonth-1,1);
                    let day = date.setDate(date.getDate()-i);
                    this.days.push(new Date(day))
                }

                for (let i=0;i<42-this.firstWeek;i++){
                    date=new Date(this.currentYear,this.currentMonth-1,1);
                    let day = date.setDate(date.getDate()+i);
                    this.days.push(new Date(day))
                }
                //console.log(this.days)
            },
            prev(day){
                let data = new Date(this.currentYear,this.currentMonth-1,1);
                data.setDate(0);
                this.getDays(data.getFullYear(), data.getMonth() + 1, '');
            },
            next(day){
                let data = new Date(this.currentYear,this.currentMonth-1,1);
                data.setDate(42);
                this.getDays(data.getFullYear(), data.getMonth() + 1, '');
            },
            //日期处理
            format(date){
                if(date =='y'){
                    return new Date().getFullYear();
                }else if(date =='m'){
                    return new Date().getMonth()+1<10?'0'+(new Date().getMonth()+1):new Date().getMonth()+1;
                }else if(date =='d'){
                    return new Date().getDate()<10?'0'+new Date().getDate() :new Date().getDate();
                }
            },
        }


    }
</script>

<style scoped lang="scss">
    @import '@/assets/css/_themeify.scss';

    .calendar {
        width: 260px;
        position: fixed;
        right: 260px;
        top: 300px;
        @include themeify {
            //background-color: themed('bg-color-white');
        }

        .calendarBox {
            padding: 0 10px;
            text-align: center;
            @include themeify {
                color: themed('text-color-default');
            }
            header {
                display: flex;
                line-height: 35px;
                font-family: "Times New Roman";
                justify-content: space-between;
                @include themeify {
                    background-color: themed('bg-color-white');
                }
                a {
                    text-decoration: none;
                    i {
                        display: block;
                        width: 35px;
                        height: 35px;
                        font-size: 20px;
                        @include themeify {
                            color: themed('text-color-default');
                            background-color: themed('bg-color-text-bg');
                        }
                        transition: 0.3s;
                    }
                }
                a:hover{
                    i{
                        transition: 0.3s;
                        @include themeify {
                            color: themed('text-color-white');
                            background-color: themed('bg-color-dark');
                        }
                    }
                }

            }
            .weekHead{
                ul{
                    display: flex;
                    @include themeify{
                        background-color: themed('bg-image-op');
                    }
                    li{
                        flex: 1;
                        height: 25px;
                        display: flex;
                        justify-content: center;
                        line-height: 25px;
                        @include themeify{
                            font-size: themed('font-size-default');
                        }
                    }
                    li:first-child{
                        @include themeify{
                            color: themed('text-color-default-q');
                        }
                    }
                    li:last-child{
                        @include themeify{
                            color: themed('text-color-default-q');
                        }
                    }
                }
            }
            .days{
                @include themeify {
                    background-color: themed('bg-color-white');
                }
                ul{
                    display: flex;
                    flex-wrap: wrap;
                    li{
                        height: 30px;
                        width: 14.2%;
                        a{
                            width: 100%;
                            height: 100%;
                            display: flex;
                            align-items: center;
                            text-decoration: none;
                            justify-content: center;
                            @include themeify {
                                font-size: themed('font-size-default-s');
                                color: themed(text-color-black);
                            }
                        }
                        transition: 0.3s;
                    }
                    .today{
                        @include themeify{
                            background-color: themed(text-color-header);
                            a{
                                color:themed(text-color-white)!important;
                            }

                        }
                    }
                    .otherDay{
                        @include themeify{
                            a{
                                color:themed(text-color-placeholder)!important; ;
                            }
                        }
                    }
                    li:nth-child(7n){
                        a{
                            @include themeify {
                                color: themed(text-color-default-q);
                            }
                        }
                    }
                    li:nth-child(7n+1){
                        a{
                            @include themeify {
                                color: themed(text-color-default-q);
                            }
                        }
                    }
                    li:hover{
                        transition:0.3s;
                        @include themeify {
                            background-color: themed(bg-color-verifycode)
                        }
                        a{
                            @include themeify {
                                color: themed(text-color-header)!important;
                            }
                        }
                    }
                }
            }
        }
    }
</style>
