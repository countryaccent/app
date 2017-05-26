<template>
    <div class="look">
        <look-header />
        <look-nav />
        <div class="test-content">
            <love-page />
        </div>
    </div>
</template>
<style>
    .look {
    }
    .test-content {
        height: 1000px;
    }
</style>
<script>
    import lookHeader from './header.vue';
    import lookNav from './nav.vue';
    import lovePage from './love/love.vue';
    Vue.component('look-header',lookHeader);
    Vue.component('look-nav',lookNav);
    Vue.component('love-page',lovePage);
    export default {
        data: function() {
            return {

            }
        },
        methods: {

        }
    }
</script>