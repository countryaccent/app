<template>
  <div class="layout">
    <div class="header">
        <div class="search">
            <text class="search-icon">&#xe6ac;</text>
        </div>
        <div class="title">
            <text class="title-txt">{{target}}</text>
        </div>
        <div class="publish">
            <text class="publish-icon">&#xe6b9;</text>
        </div>
    </div>
    <div class="nav">
        <div class="nav-item">
            <text class="item-txt">逗乐</text>
        </div>
        <div class="nav-item">
            <text class="item-txt">美景</text>
        </div>
        <div class="nav-item">
            <text class="item-txt">爱情</text>
        </div>
        <div class="nav-item">
            <text class="item-txt">故事</text>
        </div>
        <div class="nav-item">
            <text class="item-txt">财富</text>
        </div>
    </div>
    <waterfall class="page" ref="waterfall"
  v-bind:style="{padding:padding}"
  :column-width="columnWidth" :column-count="columnCount" :column-gap="columnGap"
  :show-scrollbar="showScrollbar" :scrollable="scrollable"
  @scroll="recylerScroll" @loadmore="loadmore" loadmoreoffset=3000
  >
  <refresh class="refresh" @refresh="onrefresh" @pullingdown="onpullingdown" :display="refreshing ? 'show' : 'hide'">
      <loading-indicator class="indicator"></loading-indicator>
      <text class="refreshText">{{refreshText}}</text>
    </refresh>
    <cell v-for="(item, index) in items" :key="item.src" class="cell">
        <div class="item">
        <text v-if="item.name" class="itemName">{{item.name}}</text>
        <image class="itemPhoto" :src="item.src"></image>
        <text v-if="item.desc" class="itemDesc">{{item.desc}}</text>
        <text v-if="item.behaviourName" class="itemClickBehaviour"> {{item.behaviourName}}</text>
      </div>
    </cell>
  </waterfall>
    <div class="nav-b">
        <div class="b-item">
            <text class="b-txt-icon">&#xe699;</text>
            <text class="b-txt">看看</text>
        </div>
        <div class="b-item">
            <text class="b-txt-icon">&#xe69b;</text>
            <text class="b-txt">聊天</text>
        </div>
        <div class="b-item">
            <text class="b-txt-icon">&#xe696;</text>
            <text class="b-txt">游戏</text>
        </div>
        <div class="b-item">
            <text class="b-txt-icon">&#xe698;</text>
            <text class="b-txt">乡购</text>
        </div>
        <div class="b-item">
            <text class="b-txt-icon">&#xe6b8;</text>
            <text class="b-txt">我</text>
        </div>
    </div>
  </div>

</template>

<style>
  .header {
    height: 120px;
    padding: 0 20px 0 20px;
    background-color: #D33D3E;
    flex-direction: row;
    align-items:center;
    justify-content: center;
  }
  .search {
    flex: 1;
  }
  .search-icon {
    font-family:iconfont;
    color:#FFF;
    font-size:54px;
  }
  .title {
    flex: 1;
  }
  .title-txt {
    color:#FFF;
    text-align:center;
    font-size: 42px;
  }
  .publish {
    flex: 1;
  }
  .publish-icon {
    font-family:iconfont;
    color:#FFF;
    font-size:64px;
    font-weight: bold;
    text-align: right;
  }

  .nav {
    background-color:#F6F5F3;
    height:90px;
    flex-direction: row;
    align-items:center;
    justify-content: center;
  }
  .nav-item {
    flex: 1;
  }
  .item-txt {
      font-size: 40px;
      text-align: center;
  }

  .nav-b {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    background-color:#F9F9F9;
    border-top-width: 1px;
    border-color: #B2B2B2;
    border-style: solid;
    height:120px;
    flex-direction: row;
    align-items:center;
    justify-content: center;
  }
  .b-item {
      flex: 1;
  }
  .b-txt-icon {
      font-family:iconfont;
      font-size:42px;
      text-align: center;
      padding-bottom: 8px;
  }
  .b-txt {
      font-size:28px;
      text-align: center;
  }


  .page {
    background-color: #EFEFEF;
  }
  .refresh {
    height: 128;
    width: 750;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }
  .refreshText {
    color: #888888;
    font-weight: bold;
  }
  .indicator {
    color: #888888;
    height: 40;
    width: 40;
    margin-right: 30;
  }
  .cell {
    padding-top: 6;
    padding-bottom: 6;
  }
  .item {
    background-color: #FFFFFF;
    align-items: center;
  }
  .itemName {
    font-size:28;
    color:#333333;
    line-height:42;
    text-align:left;
    margin-top: 24;
  }
  .itemPhoto {
    margin-top: 18;
    width: 220;
    height: 220;
    margin-bottom: 18;
  }
  .itemDesc {
    font-size:24;
    margin:12;
    color:#999999;
    line-height:36;
    text-align:left;
  }
  .itemClickBehaviour {
    font-size:36;
    color:#00cc99;
    line-height:36;
    text-align:center;
    margin-top: 6;
    margin-left: 24;
    margin-right: 24;
    margin-bottom: 30;
  }
</style>

<script>
  export default {
    data: {
      target: '看看',
      items:  [
        {
          src:'https://gw.alicdn.com/tps/TB1Jl1CPFXXXXcJXXXXXXXXXXXX-370-370.jpg',
          name: 'Thomas Carlyle',
          desc:'Genius only means hard-working all one\'s life',
          behaviourName: 'Change count',
          behaviour: 'changeColumnCount'
        },
        {
          src:'https://gw.alicdn.com/tps/TB1Hv1JPFXXXXa3XXXXXXXXXXXX-370-370.jpg',
          desc:'The man who has made up his mind to win will never say "impossible "',
          behaviourName: 'Change gap',
          behaviour: 'changeColumnGap'
        },
        {
          src:'https://gw.alicdn.com/tps/TB1eNKuPFXXXXc_XpXXXXXXXXXX-370-370.jpg',
          desc:'There is no such thing as a great talent without great will - power',
          behaviourName: 'Show scrollbar',
          behaviour: 'showScrollbar',
        },
        {
          src:'https://gw.alicdn.com/tps/TB1DCh8PFXXXXX7aXXXXXXXXXXX-370-370.jpg',
          name:'Addison',
          desc:'Cease to struggle and you cease to live',
          behaviourName: 'Change width',
          behaviour: 'changeColumnWidth',
        },
        {
          src:'https://gw.alicdn.com/tps/TB1ACygPFXXXXXwXVXXXXXXXXXX-370-370.jpg',
          desc:'A strong man will struggle with the storms of fate',
          behaviourName: 'Listen appear',
          behaviour: 'listenAppear',
        },
        {
          src:'https://gw.alicdn.com/tps/TB1IGShPFXXXXaqXVXXXXXXXXXX-370-370.jpg',
          name:'Ruskin',
          desc:'Living without an aim is like sailing without a compass',
          behaviourName: 'Set scrollable',
          behaviour: 'setScrollable',
        },
        {
          src:'https://gw.alicdn.com/tps/TB1xU93PFXXXXXHaXXXXXXXXXXX-240-240.jpg',
          behaviourName: 'waterfall padding',
          behaviour: 'setPadding',
        },
        {
          src:'https://gw.alicdn.com/tps/TB19hu0PFXXXXaXaXXXXXXXXXXX-240-240.jpg',
          name:'Balzac',
          desc:'There is no such thing as a great talent without great will - power',
          behaviourName: 'listen scroll',
          behaviour: 'listenScroll',
        },
        {
          src:'https://gw.alicdn.com/tps/TB1ux2vPFXXXXbkXXXXXXXXXXXX-240-240.jpg',
          behaviourName: 'Remove cell',
          behaviour: 'removeCell',
        },
        {
          src:'https://gw.alicdn.com/tps/TB1tCCWPFXXXXa7aXXXXXXXXXXX-240-240.jpg',
          behaviourName: 'Move cell',
          behaviour: 'moveCell',
        }
      ],
      padding: 0,
      columnCount: 2,
    columnGap: 12,
    columnWidth: 'auto',
    contentOffset: '0',
      refreshing: false,
      showHeader: true,
        showScrollbar: false,
        scrollable: true,
        showStickyHeader: false,
        appearImage: null,
        disappearImage: null,
        stickyHeaderType: 'none',
      refreshText: '↓   pull to refresh...',
    },
    created: function() {
        //http://www.iconfont.cn/
        var domModule=weex.requireModule("dom");
        domModule.addRule('fontFace',{
            'fontFamily':'iconfont',
            'src':"url(\'//at.alicdn.com/t/font_qrsnh867tnyx2yb9.ttf\')"
        });
    },
    methods: {
      update: function (e) {
        this.target = 'Weex'
        console.log('target:', this.target)
      },
      onrefresh (event) {
        this.refreshing = true
        this.refreshText = "loading..."
        setTimeout(() => {
          this.refreshing = false
          this.refreshText = '↓   pull to refresh...'
        }, 2000)
      },

      onpullingdown (event) {
        // console.log(`${event.pullingDistance}`)
        if (event.pullingDistance < -64) {
          this.refreshText = '↑   release to refresh...'
        } else {
          this.refreshText = '↓   pull to refresh...'
        }
      },
      recylerScroll: function(e) {
        this.contentOffset = e.contentOffset.y
      },
      loadmore: function(e) {
        console.log('receive loadmore event')
        // this.$refs.waterfall.resetLoadmore()
      },
    }
  }
</script>
