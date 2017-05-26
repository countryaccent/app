<template>
    <div class="nav">
        <div class="item">
            <text class="txt">逗乐</text>
        </div>
        <div class="item">
            <text class="txt">美景</text>
        </div>
        <div class="item">
            <text class="txt" style="color: #D33F3F;">乡爱</text>
        </div>
        <div class="item">
            <text class="txt">故事</text>
        </div>
    </div>
</template>
<style>
    .nav {
        height: 64px;
        background-color: #F4F4F4;
        border-bottom-width: 1px;
        border-color: #f2f2f2;
        flex-direction: row;
        align-items: center;
    }
    .item {
        flex: 1;
        height: 64px;
        margin-left: 20px;
        margin-right: 20px;
    }
    .txt {
        font-size: 32px;
        height: 64px;
        line-height: 64px;
        text-align: center;
    }
</style>
<script>
    export default {
        data: function() {
            return {

            }
        },
        methods: {

        }
    }
</script>