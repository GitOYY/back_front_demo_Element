<template>
    <div>
        <div class="header_container">
            <div class="logo">
                B-S management &nbsp;后台管理系统
            </div>
            <div class="user">
                <el-dropdown @command="handleCommand" menu-align='start' trigger="click">
                    <span class="el-dropdown-link">
                        <img :src="baseImgPath + adminInfo.avatar" class="avator">
                        <span class="user_name">{{adminInfo.user_name}}</span>
                    </span>
                    <el-dropdown-menu slot="dropdown">
                        <el-dropdown-item command="home">首页</el-dropdown-item>
                        <el-dropdown-item command="signout">退出</el-dropdown-item>
                    </el-dropdown-menu>
                </el-dropdown>
            </div>
        </div>
    </div>
</template>

<script>
import {signout} from '@/api/getData'
import {baseImgPath} from '@/config/env'
import {mapActions, mapState} from 'vuex'

export default {
    data(){
        return {
            baseImgPath,
        }
    },
    created(){
        if (!this.adminInfo.id) {
            this.getAdminData()
        }
    },
    computed: {
        ...mapState(['adminInfo']),
    },
    methods: {
        ...mapActions(['getAdminData']),
        async handleCommand(command) {
            if (command == 'home') {
                this.$router.push('/manage');
            }else if(command == 'signout'){
                const res = await signout()
                if (res.status == 1) {
                    this.$message({
                        type: 'success',
                        message: '退出成功'
                    });
                    this.$router.push('/');
                }else{
                    this.$message({
                        type: 'error',
                        message: res.message
                    });
                }
            }
        },
    }
}
</script>

<style lang="less">
	@import '../style/mixin';
	.header_container{
		background-color: #324057;
		height: 60px;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        padding: 0px 50px 0px 50px;
	}
    .logo{
        color: white;
        font-size: 28px;
        font-family: '华文行楷';
    }
    .user{
        display: flex;
        align-items: center;
    }
    .el-dropdown-link{
        display: flex;
        flex-direction: row;
        align-items: center;
        color: white;
        cursor: pointer;
    }
    .user_name{
        padding-left: 10px;
        .el-icon-arrow-down el-icon--right{
            font-size: 5px;
        }
    }
	.avator{
		.wh(36px, 36px);
		border-radius: 50%;
        display: flex;
        align-items: center;
	}
	.el-dropdown-menu__item{
        text-align: start;
    }

</style>
