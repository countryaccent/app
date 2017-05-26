<template>
    <div class="layout">
        <look-index />
        <a href="http://192.168.199.167:8080/dist/app.weex.js" class="link">
            <text>全屏</text>
        </a>
    </div>
</template>

<style>
    .layout {

    }
    .link {
        position: fixed;
        left: 0;
        width: 80px;
        height: 80px;
        background-color: #CCC;
        bottom: 50px;
    }
</style>

<script>
    import lookIndex from './look/index.vue';
    Vue.component('look-index',lookIndex);
    export default {
        data: function() {
            return {

            }
        },
        created: function() {
        },
        methods: {
    
        }
    }
</script>
