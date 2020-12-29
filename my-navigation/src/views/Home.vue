<template>
    <div class="navCantent">
        <header class=".header">
            <nav id="nav">
                <img src="../assets/img/logo1.jpg" alt="">
                <el-menu v-if="!selectNeNav"
                         style="background-color :#4953e9;"
                         :default-active="activeIndex2"
                         class="el-menu-demo"
                         mode="horizontal"
                         background-color="#545c64"
                         text-color="#fff"
                         active-text-color="#ffd04b">
                    <el-menu-item index="1">首页</el-menu-item>
                    <el-menu-item index="2">关于Lambda</el-menu-item>
                    <el-menu-item index="3">开发者文档</el-menu-item>
                    <el-menu-item index="4">钱包</el-menu-item>
                    <el-menu-item index="5">Lambda Eco</el-menu-item>
                    <el-menu-item index="6">技术探索</el-menu-item>
                    <el-submenu index="2">
                        <template slot="title">公告栏</template>
                        <el-menu-item index="2-1">最新活动</el-menu-item>
                        <el-menu-item index="2-2">项目周报</el-menu-item>
                        <el-menu-item index="2-3">帮助中心</el-menu-item>
                    </el-submenu>
                    <el-submenu index="3">
                        <template slot="title">中文</template>
                        <el-menu-item index="3-1">简体中文</el-menu-item>
                        <el-menu-item index="3-2">English</el-menu-item>
                    </el-submenu>
                </el-menu>
                <div v-if="selectNeNav" class="oneAcrossContent" @click="drawer=true">
                    <span class="oneAcross"></span>
                    <span class="oneAcross"></span>
                    <span class="oneAcross"></span>
                </div>
            </nav>
        </header>
        <el-drawer
                size="25%"
                :visible.sync="drawer"
                :direction="direction"
        >
            <div class="img imgPosition">
                <img  src="../assets/img/logo3.jpg" alt="">
            </div>
            <div class="aside">
                <el-row class="tac">
                    <el-col :span="12" style="width: 100%">
                        <!-- <h5>自定义颜色</h5> -->
                        <el-menu
                                default-active="2"
                                class="el-menu-vertical-demo"
                                background-color="#545c64"
                                text-color="#595959"
                                active-text-color="#1890ff">
                            <el-menu-item index="2">
                                <!-- <i class="el-icon-menu"></i> -->
                                <span slot="title">首页</span>
                            </el-menu-item>
                            <el-menu-item index="3">
                                <!-- <i class="el-icon-menu"></i> -->
                                <span slot="title">关于Lambda</span>
                            </el-menu-item>
                            <el-menu-item index="4">
                                <!-- <i class="el-icon-setting"></i> -->
                                <span slot="title">开发者文档</span>
                            </el-menu-item>
                            <el-menu-item index="5">
                                <!-- <i class="el-icon-setting"></i> -->
                                <span slot="title">钱包</span>
                            </el-menu-item>
                            <el-menu-item index="6">
                                <!-- <i class="el-icon-setting"></i> -->
                                <span slot="title">Lambda Eco</span>
                            </el-menu-item>
                            <el-menu-item index="7">
                                <!-- <i class="el-icon-setting"></i> -->
                                <span slot="title">技术探索</span>
                            </el-menu-item>
                            <el-submenu index="1">
                                <template slot="title">
                                    <!-- <i class="el-icon-location"></i> -->
                                    <span>公告栏</span>
                                </template>
                                <el-menu-item-group>
                                    <el-menu-item index="1-1">最新活动</el-menu-item>
                                    <el-menu-item index="1-2">项目周报</el-menu-item>
                                    <el-menu-item index="1-3">帮助中心</el-menu-item>
                                </el-menu-item-group>
                            </el-submenu>
                            <el-submenu index="2">
                                <template slot="title">
                                    <!-- <i class="el-icon-location"></i> -->
                                    <span>中文</span>
                                </template>
                                <el-menu-item-group>

                                    <el-menu-item index="2-1">中文</el-menu-item>
                                    <el-menu-item index="2-2">English</el-menu-item>
                                </el-menu-item-group>
                            </el-submenu>
                        </el-menu>
                    </el-col>
                </el-row>
            </div>


        </el-drawer>
        <!-- <router-view></router-view> -->
    </div>


</template>

<script>
    import '../assets/css/nav.css'

    export default {
        data() {
            return {
                activeIndex: '1',
                activeIndex2: '1',
                screenWidth: null,
                selectNeNav: false,
                drawer: false,
                direction: 'rtl',
            };
        },
        watch: {
            screenWidth: {

                handler(newVal) {
                    if (newVal < 1224) {
                        this.selectNeNav = true
                    }
                    if (newVal > 1224) {
                        this.selectNeNav = false
                    }
                },
                immediate: true
            }
        },
        mounted() {
            this.screenWidth = document.body.clientWidth;
            window.onresize = () => {
                return (() => {
                    this.screenWidth = document.body.clientWidth;
                })();
            };
        },
        methods: {}
    }
</script>
<style lang="stylus">
    .navCantent {
        width: 100%
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        background-color: #4953e9;
    }

    .navCantent .header {
        width: 100%;
        background-color: #4953e9;
        display: flex;
        justify-content: center;
    }

    nav {
        width: 1024px;
        height: 80px;
        display: flex;
        justify-content: space-between;
        align-items: center;

    }

    .el-menu {
        background-color: #4953e9 !important;
    }

    .el-menu--horizontal {
        background-color: #4953e9 !important;
    }

    .el-menu-item {
        background-color: #4953e9 !important;
    }

   .el-submenu__title {
        background-color: #4953e9 !important;
    }

    .el-menu.el-menu--horizontal {
        border-bottom: none !important
    }

    .aside.el-menu {
        background-color: #fff !important;
        border-right: solid 0 #e6e6e6
        color :black
    }

    .aside .el-menu--horizontal {
        background-color: #fff !important;
        color :black
    }

    .aside .el-menu-item {
        background-color: #fff !important;
        
    }

    .aside .el-submenu__title {
        background-color: #fff !important;
        
    }

    .aside .el-menu.el-menu--horizontal {
        border-bottom: none !important
        color :black
    }

    .aside .el-menu-item-group__title {
        background-color: #fff !important;
        color :black
    }
  .imgPosition{
    position: absolute;
    width:153px;
    height:44px;
    top: -60px;
    left: 20px;
  }
  .tac{
    width :100%;
    height: 500px;
    overflow-y: auto;
  }
  .img{
    position:relative;
  }
  
    nav img {
        width: 140px;
        height: 40px;

    }

    .oneAcrossContent {
        width 20px;
        height 30px;
        margin-right:190px;
    }

    .oneAcross {
        display: block;
        width 100%
        height 5px;
        border-bottom 3px solid #fff;
    }

</style>