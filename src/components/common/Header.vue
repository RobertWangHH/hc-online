<template>
    <div class="hc-header-box">
        <div class="hc-header">
            <div class="logo">LOGO</div>
            <div class="city">
                <el-button :plain="true" type="info" icon="view">选择城市</el-button>
            </div>
            <div class="user-info">
                <el-dropdown @command="handleCommand">
                <span class="el-dropdown-link">
                    <img class="user-logo" src="../../../static/img/img.jpg">
                    {{username}}
                    <i class="el-icon-caret-bottom el-icon--right"></i>
                </span>
                    <el-dropdown-menu slot="dropdown">
                        <el-dropdown-item command="loginout">个人中心</el-dropdown-item>
                        <el-dropdown-item command="loginout">退出</el-dropdown-item>
                    </el-dropdown-menu>
                </el-dropdown>
            </div>
        </div>
        <div class="hc-menu-box">
            <div class="hc-menu">
                <ul class="tabs">
                    <li class="menu-item"><a>找厂房</a></li>
                    <li class="menu-item"><a>找客户</a></li>
                    <li class="menu-item"><a>找服务商</a></li>
                    <li class="menu-item"><a>委托展示</a></li>
                    <li class="menu-item"><a>政府招商</a></li>
                    <li class="menu-item"><a>不良资产</a></li>
                    <li class="menu-item"><a>资源变现</a></li>
                </ul>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                name: 'linxin'
            }
        },
        computed:{
            username(){
                let username = localStorage.getItem('ms_username');
                return username ? username : this.name;
            }
        },
        methods:{
            handleCommand(command) {
                if(command == 'loginout'){
                    localStorage.removeItem('ms_username')
                    this.$router.push('/login');
                }
            }
        }
    }
</script>
<style scoped>
    .hc-header {
        width: 1180px;
        height: 64px;
        margin: 0 auto;
    }
    .hc-header-box .hc-menu-box{
        background: #62ab00;
        position: relative;
        width: 100%;
    }
    .hc-header-box .hc-menu{
        height: 48px;
        top: 64px;
        width: 1180px;
        margin: 0 auto;
    }
    .hc-header-box .hc-menu .tabs{
        float: left;
        list-style: none;
    }
    .hc-header-box .hc-menu .tabs .menu-item{
        float: left;
        height: 48px;
        line-height: 48px;
        position: relative;
        z-index: 99;
    }
    .hc-header-box .hc-menu .tabs .menu-item a{
        padding: 0 17px;
        font-size: 18px;
        display: block;
        font-family: "Microsoft YaHei","微软雅黑","Hiragino Sans GB",tahoma,arial,simhei;
        color: #fff;
    }
    .hc-header-box .hc-menu .tabs .menu-item:hover{
        cursor: pointer;
        background-color: #528e01;
        border-radius: 2px;
    }
    .hc-header .logo{
        float: left;
        width:150px;
        text-align: center;
        line-height: 64px;
    }
    .hc-header .city{
        float: left;
        line-height: 64px;
    }
    .user-info {
        float: right;
        color: #666;
        line-height: 64px;
        height: 64px;
    }
    .user-info .el-dropdown{
        height: 64px;
        cursor: pointer;
    }
    .user-info .el-dropdown-link{
        position: relative;
        top: -10px;
        font-size: 12px;
    }
    .user-info img{
        width: 50px;
        height: 50px;
        border-radius: 50%;
        position: relative;
        top: 15px;
        margin-right: 5px;
    }
    .el-dropdown-menu .el-dropdown-menu__item{
        font-size:14px;
        text-align:center;
    }
</style>
