<template>
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
        <image class="itemPhoto" :src="item.src" :style="{height:item.height}"></image>
        <text v-if="item.behaviourName" class="itemClickBehaviour"> {{item.behaviourName}}</text>
      </div>
    </cell>
    <div class="fixedItem" @click="scrollToTop">
      <text class="fixedText">Top</text>
    </div>
  </waterfall>
</template>

<style>
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
    padding-top: 5;
    padding-bottom: 5;
  }
  .item {
    background-color: #FFFFFF;
    align-items: center;
  }
  .itemPhoto {
    width: 370;
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
  .fixedItem {
    position: fixed;
    width:78;
    height:78;
    background-color:#00cc99;
    right: 32;
    bottom: 32;
    border-radius: 39;
    align-items: center;
    justify-content: center;
  }
  .fixedText {
    font-size: 36;
    color: white;
    line-height: 36;
  }

</style>

<script>
  export default {
    data: function() {
      const items = [
        {
          src:'http://img.hb.aicdn.com/2d3afce7b4da9eeefcf3a89741aa330d619ad574bda1f-68O6VR_fw236',
          height: 555,
          name: 'Thomas Carlyle',
          desc:'Genius only means hard-working all one\'s life',
          behaviourName: 'Change count',
          behaviour: 'changeColumnCount'
        },
        {
          src:'//img.hb.aicdn.com/e959d534f14decd5866ec3a6b2a40e43bff8916fdfc60-5BsQAq_fw236',
          height: 462,
          desc:'The man who has made up his mind to win will never say "impossible "',
          behaviourName: 'Change gap',
          behaviour: 'changeColumnGap'
        },
        {
          src:'//img.hb.aicdn.com/e67e9954405db3bbf250778dee4819f50ae2e4352a20f-54umaP_fw236',
          height: 470,
          desc:'There is no such thing as a great talent without great will - power',
          behaviourName: 'Show scrollbar',
          behaviour: 'showScrollbar',
        },
        {
          src:'//img.hb.aicdn.com/a706a0ce15516166407c1784d392e60c03f4acdb2ec8d-WZU5sj_fw236',
          height: 555,
          name:'Addison',
          desc:'Cease to struggle and you cease to live',
          behaviourName: 'Change width',
          behaviour: 'changeColumnWidth',
        },
        {
          src:'//img.hb.aicdn.com/254104731142f7020edca8cf9f5cb4e392d04eb81f824-vYLEl5_fw236',
          height: 618,
          desc:'A strong man will struggle with the storms of fate',
          behaviourName: 'Listen appear',
          behaviour: 'listenAppear',
        },
        {
          src:'//img.hb.aicdn.com/a1acb1017f310d07303fe70d561c113d5beb19c817629-wgf5Kw_fw236',
          height: 563,
          name:'Ruskin',
          desc:'Living without an aim is like sailing without a compass',
          behaviourName: 'Set scrollable',
          behaviour: 'setScrollable',
        },
        {
          src:'//img.hb.aicdn.com/6ae398922d4b7c89685ec89b1b4be48b74f072a827939-OiRyED_fw236',
          height: 555,
          behaviourName: 'waterfall padding',
          behaviour: 'setPadding',
        },
        {
          src:'//img.hb.aicdn.com/e3c82f9ef4325ed16dffbefe8b1bae2bea38f1de1e99c-YOcaLh_fw236',
          height: 575,
          name:'Balzac',
          desc:'There is no such thing as a great talent without great will - power',
          behaviourName: 'listen scroll',
          behaviour: 'listenScroll',
        },
        {
          src:'//img.hb.aicdn.com/9df8a542b191079ca97dbde9dc5b6def104717da1fce8-nqkvp4_fw236',
          height: 462,
          behaviourName: 'Remove cell',
          behaviour: 'removeCell',
        },
        {
          src:'//img.hb.aicdn.com/2332856a7a8f5ce089cddc9892e8673c14650c0920f1e-fT51fP_fw236',
          height: 248,
          behaviourName: 'Move cell',
          behaviour: 'moveCell',
        }
      ]

      let repeatItems = [];
      for (let i = 0; i < 3; i++) {
        repeatItems.push(...items)
      }

      return {
        padding: 0,
        refreshing: false,
        refreshText: '↓   pull to refresh...',
        columnCount: 2,
        columnGap: 10,
        columnWidth: 'auto',
        contentOffset: '0',
        showScrollbar: false,
        scrollable: true,
        showStickyHeader: false,
        appearImage: null,
        disappearImage: null,
        stickyHeaderType: 'none',
        items: repeatItems
      }
    },

    methods: {
      recylerScroll: function(e) {
        this.contentOffset = e.contentOffset.y
      },
      loadmore: function(e) {
        console.log('receive loadmore event')
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
      }
    }
  }
</script>
