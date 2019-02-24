<template>
    <div id="mainPage">
        <div class="mainHead"  v-if="isRefresh">
            <el-row>
                <el-col :span="3"><div style="opacity:0">1</div></el-col>
                <el-col :span="19">
                    <div class="wangyiLogo">
                        <h2>网易云音乐</h2>
                    </div>
                    <div class="headContent">
                        <ul>
                            <li v-for="(el,idx) in navLists" :key="idx" :class="idx==index?'active':''" @click="clickRow(el,idx)">{{el.name}}</li>
                        </ul>
                    </div>
                    <div class="rightSign">
                        右侧的东西
                    </div>
                </el-col>
                <el-col :span="2"><div style="opacity:0">3</div></el-col>
            </el-row>
        </div>
        <div class="mainBody">
            <component :is='currentView' v-if="isRefresh"></component>
        </div>
    </div> 
</template>

<script>
    import WangyiMusic from '@/components/WangyiMusic'
    import MyMusic from '@/components/MyMusic'
    import FindMusic from '@/components/FindMusic'
    import HelloWorld from '@/components/HelloWorld'
    import Friend from '@/components/Friend'
    import Shop from '@/components/Shop'
    import Musicien from '@/components/Musicien'
    import DownLoad from '@/components/DownLoad'
    import RightSign from '@/components/RightSign'

    export default {
        name:'MainPage',
        components:{
            WangyiMusic,
            FindMusic,
            MyMusic,
            HelloWorld,
            Friend,
            Shop,
            Musicien,
            DownLoad,
            // RightSign

        },
        data(){
            return {
                navLists:[
                    // {'name':'网易云音乐','item':'WangyiMusic'},
                    {'name':'发现音乐','item':'FindMusic'},
                    {'name':'我的音乐','item':'MyMusic'},
                    {'name':'朋友','item':'Friend'},
                    {'name':'商城','item':'Shop'},
                    {'name':'音乐人','item':'Musicien'},
                    {'name':'下载客户端','item':'DownLoad'},
                    // {'name':'右侧的东西','class':'lastLi','item':'RightSign'}
                    ],
                currentView:'',
                isRefresh:true,
                index:0,
                // imgUrl:require("")

            }
        },
        mounted:function (){
            this._initEx();
        },
        methods:{
            _initEx:function(){
                this.currentView = 'FindMusic';
            },
            clickRow:function(el,idx){
                console.log(el);
                console.log(idx);
                this.currentView = el.item;
                this.isRefresh = false;
                this.index=idx;
                this.$nextTick(()=>{
                    this.isRefresh = true;
                })
                
            }


        }
    }
</script>

<style scoped>
    .mainHead{
        width:100%;
        height: 70px;
        background-color: #242424;
        color: #fff;
    }
    .mainHead>div{
        height: 70px;
        line-height: 70px;
        width: 100%;
    }
    .wangyiLogo{
        width:150px;
        height: 70px;
        line-height: 70px;
        position: absolute;
        top: 0;
        left: -50px;
        font-size:22px;
        font-weight: 500;
        font-family: Arial, Helvetica, sans-serif;
    }
    .wangyiLogo h2{
        margin: 15px auto;
        width:175px;
        height:40px;
        background: url(../assets/images/topbar.png) no-repeat 0 -15px;
        text-indent: -9999px;
    }
    .mainHead .el-row .el-col-19{
        position: relative;
    }
    .headContent{
        width: calc(100% - 100px);
        height:70px;
        margin-left: 120px;
    }
    .headContent li{
        list-style: none;
        float: left;
        height: 100%;
        width:100px;
        font-size: 14px;
        color: #ccc;
    }
    li.active{
        background-color: #000;
        color: #fff;
        position: relative;
    } 
    li.active::after{
        content:"";
        width:12px;
        height:6px;
        background: url(../assets/images/topbar.png) no-repeat -227px 0px;
        position: absolute;
        left: 50%;
        bottom: 0;
        transform: translateX(-50%);
    } 
    .headContent li:hover{
        background-color: #000;
        cursor: pointer;
    }
   .rightSign{
       width: 350px;
       height:70px;
       line-height: 70px;
       position: absolute;
       top: 0;
       right: 0;
       color:#fff;
   }
</style>
