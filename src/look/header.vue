<template>
    <div class="header">
        <div class="h-search">
            <text class="hs-txt" @click="toSerachPage()">&#xe6ac;</text>
        </div>
        <div class="h-title">
            <text class="ht-txt">看看</text>
        </div>
        <div class="h-publish">
            <text class="hp-txt" @click="openPublishDialog()">&#xe6b9;</text>
        </div>
    </div>
</template>
<style>
    .header {
        position: relative;
        height: 120px;
        background-color: #D33D3E;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        padding-top: 40px;
    }
    .h-search {
        position: absolute;
        left: 25px;
        top: 60px;
    }
    .h-title {
        flex: 1;
    }
    .h-publish {
        position: absolute;
        right: 25px;
        top: 50px;
    }
    .hs-txt {
        font-family: iconfont;
        color: #FFF;
        font-size: 40px;
        width: 40px;
    }
    .hs-txt:active {
        color: #CCC;
    }
    .ht-txt {
        text-align: center;
        color: #FFF;
        font-weight: bold;
        font-size: 32px;
    }
    .hp-txt {
        font-family: iconfont;
        color: #FFF;
        font-size: 60px;
        width: 60px;
    }
    .hp-txt:active {
        color: #CCC;
    }
</style>
<script>
    const dom = weex.requireModule("dom");
    export default {
        data: function() {
            return {

            }
        },
        created: function() {
            dom.addRule('fontFace',{
                'fontFamily': 'iconfont',
                'src': 'url("//at.alicdn.com/t/font_qrsnh867tnyx2yb9.ttf")'
            });
        },
        methods: {
            toSerachPage: function() {

            },
            openPublishDialog: function() {
                
            }
        }
    }
</script>