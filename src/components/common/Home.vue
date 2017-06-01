<template>
    <div class="wrapper">
        <v-head></v-head>
        <div class="con-box">
            <v-sidebar></v-sidebar>
            <div class="content">
                <transition name="move" mode="out-in"><router-view></router-view></transition>
            </div>
        </div>
    </div>
</template>

<script>
    import vHead from './Header.vue';
    import vSidebar from './Sidebar.vue';
    export default {
        components:{
            vHead, vSidebar
        }
    }
</script>

<style scoped>
    .con-box{
        width: 1180px;
        height: auto;
        margin: 0 auto;
        position: relative;
    }
</style>
