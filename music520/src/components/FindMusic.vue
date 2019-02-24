<template>
    <div id="FindMusic">
        <!-- <div class="navBar">
            <ul>
                <li v-for="(el,idx) in findLists" :key="idx" @click="clickFindRow(el,idx)" :class="idx==index?'active':''"><a>{{el.name}}</a></li>
            </ul>
        </div>
        <div class="findBody">
            <component :is="currentView"></component>
        </div> -->


        <div class="slideStyle">
          
            <el-slider v-model="value1" :show-tooltip="false" v-if="isRefresh"></el-slider>
            <div>
                <input v-model="value0">
                <input v-model="value2" @blur="inputChange">
            </div>
            <!-- <div class="white"></div>
            <div class="blue">
                <span>

                </span>
            </div> -->
            

        </div>
    </div>
</template>
<script>
    import Slider from '@/components/Slider'
    import WangyiMusic from '@/components/WangyiMusic'
    import MyMusic from '@/components/MyMusic'
    // import FindMusic from '@/components/FindMusic'
    import HelloWorld from '@/components/HelloWorld'
    import Friend from '@/components/Friend'
    import Shop from '@/components/Shop'
    import Musicien from '@/components/Musicien'
    import DownLoad from '@/components/DownLoad'
    import RightSign from '@/components/RightSign'
    export default {
        name:'FindMusic',
        components:{},
        data(){
            return {
                index:0,
                findLists:[
                    // {'name':'推荐','item':'FindMusic'},
                    {'name':'排行榜','item':'MyMusic'},
                    {'name':'歌单','item':'Friend'},
                    {'name':'主播电台','item':'Shop'},
                    {'name':'歌手','item':'Musicien'},
                    {'name':'新碟上架','item':'Musicien'}
                ],
                currentView:'',
                value0:0,
                value1:20,
                value2:20,
                value3:20,
                isRefresh:true
            }
        },
        mouted(){
            
        },
        methods:{
            clickFindRow:function(el,idx){
                console.log(el);
                this.currentView = el.item;
                this.isRefresh = false;
                this.index=idx;
                this.$nextTick(()=>{
                    this.isRefresh = true;
                })
            },
            search:function(event){
                console.log(event)
            },
            inputChange(e) {
                console.log(e);
                let number = parseInt(e.target.value);
                this.value1 = number;
            }
        },
        watch:{
            value1:function(newVal){
                this.value2 = newVal;
            },
            // value2:function(){
            //     // this.value2.
            //     this.value1=parseInt(this.value2);
            // }
          
          
        }
    }
</script>
<style scoped>
.slideStyle{
    width: 300px;
    height:200px;
    border:1px solid #000;
    position: absolute;
    top:100px;
    left:300px;
}



.navBar{
    height:34px;
    line-height: 34px;
    width:100%;
    background-color: #C20C0C;
    padding-left: 285px;
    font-size: 12px;
}
ul,li{
    margin: 0;
    padding: 0;
    list-style: none;
}
.navBar li{
    float: left;
    margin-left: 20px;
    width: 70px;
    color:#FFf;
}
.navBar li a {
   
}
.navBar li:active a{
 padding: 3px 9px;
    border: 1px solid #9B0909;
    background-color: #9B0909;
}
.white {
    margin: 30px 20px;
    width:250px;
    height:0;
    border: 4px solid pink;
    
}
.blue{
     width:50px;
    height:0;
    border: 4px solid blue;
    position: absolute;
    top:30px;
    left:20px;
}
.blue span{
    width: 16px;
    height: 16px;
    border-radius: 8px;
    background-color: yellow;
    position: absolute;
    top:-8px;
    right:-8px;
}
</style>
<style>
.slideStyle input{
    /* background: none; */
    margin: 0;
    padding: 0;
    border:1px solid #cccccc;
    width: 60px;
    height: 20px;
    line-height: 20px;
    text-align: center;
    color:#000;
    float: left;
}
.slideStyle input:nth-of-type(2){
 float: right;
}
</style>