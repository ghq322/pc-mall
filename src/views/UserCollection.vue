<template>
    <div>
        <MyHeader />
        <div class="collectionBox">
            <div class="row">
                <!-- 面包屑 -->
                <div class="crumbs">
                    <router-link  to="/">首页</router-link>
                    <div class="icon icon-right_s"></div>
                    <span class="">我的收藏</span>
                </div>
                <div class="content">
                    <UserSide />
                    <div v-if="collectionList.length != 0" class="collectionContent">
                        <div class="item" v-for="(item,index) in collectionList" :key='index'>
                            <div class="main">
                                <div @click="handleClose(item,index)" class="close icon icon-close"></div>
                                <router-link :to="'/detail?id='+item.id">
                                    <img :src="item.img" alt="item.name" />
                                </router-link>
                                <router-link :to="'/detail?id='+item.id" class="name">
                                    {{item.name}}
                                </router-link>
                                <div class="price">
                                    ￥{{item.price}}
                                </div>
                                <div class="btns">
                                    <a href="javascript:;">找相似</a>
                                    <a href="javascript:;">加入购物车</a>
                                </div>
                            </div>
                        </div>
                        <VuePage :cur="cur" :all="all" :callback="callback" />
                    </div>
                    <NoData v-else position="0 -760px" />
                </div>
            </div>
        </div>
        <MyFooter />
    </div> 
</template>
<script>
import MyHeader from "@/components/MyHeader/MyHeader.vue";
import MyFooter from "@/components/MyFooter/MyFooter.vue";
import UserSide from "@/components/UserSide/UserSide.vue";
import VuePage from "@/components/page/page.vue"

export default{
  components: {  MyHeader,  MyFooter ,UserSide,VuePage}, 
    name:"userCollection",
    data(){
        return{
            cur: 1,
            all: 8,
            collectionList:[
                {name:'男/女 轻柔色纺纱家居拖鞋',img:'https://yanxuan-item.nosdn.127.net/072a79db3d9e3f4a1d652f498311e102.png?quality=95&thumbnail=200x200&imageView',price:'43.9',id:0},
                {name:'男/女 轻柔色纺纱家居拖鞋',img:'https://yanxuan-item.nosdn.127.net/072a79db3d9e3f4a1d652f498311e102.png?quality=95&thumbnail=200x200&imageView',price:'43.9',id:1},
                {name:'男/女 轻柔色纺纱家居拖鞋',img:'https://yanxuan-item.nosdn.127.net/072a79db3d9e3f4a1d652f498311e102.png?quality=95&thumbnail=200x200&imageView',price:'43.9',id:0},
                {name:'男/女 轻柔色纺纱家居拖鞋',img:'https://yanxuan-item.nosdn.127.net/072a79db3d9e3f4a1d652f498311e102.png?quality=95&thumbnail=200x200&imageView',price:'43.9',id:1},
                {name:'男/女 轻柔色纺纱家居拖鞋',img:'https://yanxuan-item.nosdn.127.net/072a79db3d9e3f4a1d652f498311e102.png?quality=95&thumbnail=200x200&imageView',price:'43.9',id:0},
                {name:'男/女 轻柔色纺纱家居拖鞋',img:'https://yanxuan-item.nosdn.127.net/072a79db3d9e3f4a1d652f498311e102.png?quality=95&thumbnail=200x200&imageView',price:'43.9',id:1},
                {name:'男/女 轻柔色纺纱家居拖鞋',img:'https://yanxuan-item.nosdn.127.net/072a79db3d9e3f4a1d652f498311e102.png?quality=95&thumbnail=200x200&imageView',price:'43.9',id:0},
                {name:'男/女 轻柔色纺纱家居拖鞋',img:'https://yanxuan-item.nosdn.127.net/072a79db3d9e3f4a1d652f498311e102.png?quality=95&thumbnail=200x200&imageView',price:'43.9',id:1},
            ]
        }
    },
    created(){
        
    },
    mounted(){
        
    },
    methods:{
        callback(data) {
          this.cur = data;
        },
        handleClose(e,i){
            this.collectionList.splice(i,1)
        }
    },
}
</script>

<style lang="scss">
    .collectionBox{
        .content{
            display: flex;
            .collectionContent{
                width: 890px;
                margin-left: 20px;
                display: flex;
                flex-wrap: wrap;
                align-content: baseline;
                .item{
                    width: 215px;
                    height: 330px;
                    margin-right: 10px;
                    margin-bottom: 10px;
                    &:hover{
                        box-shadow: 1px 1px 8px rgba(0,0,0,.2);
                        background-color: #f4f0ea;
                    }
                    &:nth-child(4n+4){
                        margin-right: 0;
                    }
                    .main{
                        width: 100%;
                        height: 100%;
                        position: relative;
                        text-align: center;
                        font-size: 14px;
                        &:hover .close{
                            display: flex;
                        }
                        .close{
                            z-index: 2;
                            cursor: pointer;
                            display: none;
                            position: absolute;
                            top: 0;
                            right: 0px;
                            background-color: rgba(0,0,0,0.5);
                            color: #fff;
                            justify-content: center;
                            align-items: center;
                        }
                        a,img{
                            display: inline-block;
                        }
                        img{
                            width: 215px;
                            height: 200px;
                            background-color: #aaaaaa;
                        }
                        .name{
                            color: #333;
                            font-weight: bold;
                            margin-top: 10px;
                            &:hover{
                                color: #b4a078;
                            }
                        }
                        .price{
                            margin-top: 10px;
                            color:red;
                        }
                        .btns{
                            justify-content: center;
                            margin-top: 10px;
                            display: flex;
                            a{
                                height: 28px;
                                display: flex;
                                justify-content: center;
                                align-items: center;
                                width: 90px;
                                background: #F5F5F5;
                                border: 1px solid #ddd;
                                border-radius: 0;
                                &:hover{
                                    background-color: #fff;
                                }
                            }
                        }
                    }
                }
            }
        }
    }
</style>

