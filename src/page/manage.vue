<template>
    <div class="layout">
        <div class="header">
            <head-top></head-top>
        </div>
        <div class="container">
            <div class="nav">
                <el-scrollbar>
                    <el-menu :default-active="defaultActive" theme="dark" class="menu" router>
                        <el-menu-item index="manage"><i class="el-icon-menu"></i>首页</el-menu-item>
                        <el-submenu index="2">
                            <template slot="title"><i class="el-icon-document"></i>数据管理</template>
                            <el-menu-item index="userList">用户列表</el-menu-item>
                            <el-menu-item index="shopList">商家列表</el-menu-item>
                            <el-menu-item index="foodList">食品列表</el-menu-item>
                            <el-menu-item index="orderList">订单列表</el-menu-item>
                            <el-menu-item index="adminList">管理员列表</el-menu-item>
                        </el-submenu>
                        <el-submenu index="3">
                            <template slot="title"><i class="el-icon-plus"></i>添加数据</template>
                            <el-menu-item index="addShop">添加商铺</el-menu-item>
                            <el-menu-item index="addGoods">添加商品</el-menu-item>
                        </el-submenu>
                        <el-submenu index="4">
                            <template slot="title"><i class="el-icon-star-on"></i>图表</template>
                            <el-menu-item index="visitor">用户分布</el-menu-item>
                            <!-- <el-menu-item index="newMember">用户数据</el-menu-item> -->
                        </el-submenu>
                        <el-submenu index="5">
                            <template slot="title"><i class="el-icon-edit"></i>编辑</template>
                            <!-- <el-menu-item index="uploadImg">上传图片</el-menu-item> -->
                            <el-menu-item index="vueEdit">文本编辑</el-menu-item>
                        </el-submenu>
                        <el-submenu index="6">
                            <template slot="title"><i class="el-icon-setting"></i>设置</template>
                            <el-menu-item index="adminSet">管理员设置</el-menu-item>
                            <!-- <el-menu-item index="sendMessage">发送通知</el-menu-item> -->
                        </el-submenu>
                        <el-submenu index="7">
                            <template slot="title"><i class="el-icon-warning"></i>说明</template>
                            <el-menu-item index="explain">说明</el-menu-item>
                            <el-menu-item index="explain">说明</el-menu-item>
                            <el-menu-item index="explain">说明</el-menu-item>
                            <el-menu-item index="explain">说明</el-menu-item>
                            <el-menu-item index="explain">说明</el-menu-item>
                            <el-menu-item index="explain">说明</el-menu-item>
                        </el-submenu>
                </el-menu>
                </el-scrollbar>
            </div>
            <div class="content">
                <div class="breadCrumb">
                    <bread-crumb></bread-crumb>
                </div>
                <div class="router">
                    <keep-alive>
                        <router-view></router-view>
                    </keep-alive>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import headTop from '../components/headTop'
import breadCrumb from '../components/breadCrumb'

export default {
    data() {
        return {

        }
    },
    components: {
        headTop,
        breadCrumb
    },
    computed: {
        defaultActive: function(){
            return this.$route.path.replace('/', '');
        }
    },
}
</script>


<style lang="less" scoped>
	@import '../style/mixin';

    .layout{
        .wh(100%, 100%);
        position: absolute;
        display: flex;
        flex-direction: column;
        min-width: 100%;
    }
    .header{
        .wh(100%, 60px);
        line-height: 60px;
        background: #363e4f;
    }
    .container{
        .wh(100%, 100%);
        min-height: calc(100% - 60px);
        /*min-width: calc(100% - 200px);*/
        display: flex;
        flex-direction: row;
    }
    .nav{
        .wh(200px, 100%);
        min-height: calc(100% - 60px);
        background: #324057;
    }
    .menu{
        width: 200px;
    }
    .content{
        .wh(100%, 100%);
        background: white;
        display: flex;
        flex-direction: column;
        min-width: calc(100% - 200px);
    }
    .breadCrumb{
        width: 100%;
        background: #dfe6e9;
    }
    .router{
        .wh(100%, 100%);
        background: white;
        min-height: calc(100% - 110px);
        overflow: auto;
    }
</style>
