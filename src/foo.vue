<template>
  <div>
  <div class="header">
    <div class="search">LOGO</div>
    <div class="nav">
      <text>{{target}}</text>
    </div>
    <div class="publish">发布</div>
  </div>
  </div>
</template>

<style>
  .header {
    height: 100px;
    background-color: #464c5b;
  }
  .logo {
    width:50px;
  }
</style>

<script>
  export default {
    data: {
      logoUrl: 'https://alibaba.github.io/weex/img/weex_logo_blue@3x.png',
      target: 'World'
    },
    methods: {
      update: function (e) {
        this.target = 'Weex'
        console.log('target:', this.target)
      }
    }
  }
</script>
