<template>
    <div class="look">
        <look-header />
        <look-nav />
    </div>
</template>
<style>
    .look {
    }
</style>
<script>
    import lookHeader from './header.vue';
    import lookNav from './nav.vue';
    Vue.component('look-header',lookHeader);
    Vue.component('look-nav',lookNav);
    export default {
        data: function() {
            return {

            }
        },
        methods: {

        }
    }
</script>