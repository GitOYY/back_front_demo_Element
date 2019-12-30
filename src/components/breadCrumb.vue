<template>
    <div>
        <div class="breadMain">
            <div class="icon">
                <img src="../assets/img/breadCrumbSign.png" alt="">
            </div>
            <div class="breadCrumb">
                <el-breadcrumb separator="/" class="breadCrumb">
                    <el-breadcrumb-item :to="{ path: '/manage' }">首页</el-breadcrumb-item>
                    <el-breadcrumb-item v-for="(item, index) in $route.meta" :key="index">{{item}}</el-breadcrumb-item>
                </el-breadcrumb>
            </div>
        </div>
    </div>
</template>

<script>
	export default {
		name: "breadCrumb"
	}
</script>

<style lang="less" scoped>
    .breadMain{
        width: 100%;
        height: 50px;
        display: flex;
        flex-direction: row;
    }
    .icon{
        line-height: 50px;
        padding-left: 50px;
        padding-right: 15px;
        display: flex;
        align-items: center;
        img{
            width: 30px;
            height: 25px;
        }
    }
    .breadCrumb{
        line-height: 50px;
    }
</style>
