<template>
    <div id="app" class="fillcontain">
		    <router-view></router-view>
    </div>
</template>

<script>
    export default {

    }
</script>

<style lang="less">
	@import './style/common';

    //配置el的滚动条
    .el-scrollbar {
        height: 100%;
    }
    .el-scrollbar__wrap {
        overflow: scroll;
        width: 100%;
        height: 100%;
    }
</style>
