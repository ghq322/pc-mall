<template>
    <div>
        <MyHeader :headType="true"  />
        <div class="row">
            <!-- 侧栏 -->
            <UserSide />
            <!-- 内容 -->
            <div class="main">
                <NavTab :tabList="tabList" @Click="handleClick" :init='init' />
                <NoData  position="0 -1630px" />
            </div>
        </div>
        <!-- 底部 -->
        <MyFooter />
    </div> 
</template>

<script>
import MyHeader from "@/components/MyHeader/MyHeader.vue";
import MyFooter from "@/components/MyFooter/MyFooter.vue";
import UserSide from "@/components/UserSide/UserSide.vue";
import NavTab from "@/components/navTab/navTab.vue";

export default{
  components: {  MyHeader, MyFooter  ,UserSide,NavTab},
    name:"msgCenter",
    data(){
        return{
            tabList:['严选活动','我的资产','通知消息','物流助手','互动消息'],
            init:0,
            navData:[
                {text:'严选活动'},
                {text:'我的资产'},
                {text:'通知消息'},
                {text:'物流助手'},
                {text:'互动消息'},
            ]
        }
    },
    methods:{
        handleClick(i){
            if(i == this.init){
                return
            }
            this.init = i
        }
    }
}
</script>

<style lang="scss" scoped>
    .row{
        display: flex;
        margin-top:52px;
    }
    .main{
        margin-top: 20px;
        position: relative;
        width: 890px;
        margin-left: 20px;
        overflow: hidden;
        z-index: 1;
        padding-bottom: 80px;
        .commonTab{
            .innerWrap{
                overflow: hidden;
                position: relative;
                display: block;
                ul{
                    height:38px;
                    border-bottom: 2px solid #eaeaea;
                    li.item{
                        box-sizing: border-box;
                        position: relative;
                        z-index: 2;
                        float: left;
                        text-align: center;
                        cursor: pointer;
                        width: 150px;
                        padding: 10px 0;
                        height: 38px;
                        font-weight: 900;
                        font-size: 18px;
                        color: #333;
                        margin-bottom: -2px;
                        &.active{
                            border-bottom: 2px solid #b4a078;
                        }
                        &.active a {
                            color: #b4a078;
                        }
                        &:first-child a {
                            border: none;
                        }
                        a{
                            display: block;
                            width:100%;
                            font-size: 18px;
                            height: 18px;
                            line-height: 1;
                            border-left: 1px solid #eaeaea;
                            cursor: pointer;
                        }
                    }
                }
            }
        }   
        .displayContainer{

        }
    }
</style>

