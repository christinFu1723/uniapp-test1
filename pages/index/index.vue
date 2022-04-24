<template>
  <view class="content">
    <scroll-view
      scroll-x
      class="border-bottom scroll-row"
      style="height: 80rpx;"
      :scroll-into-view="scrollInto"
      scroll-with-animation
    >
      <view
        class="scroll-row-item px-3"
        style="height: 80rpx;line-height: 80rpx;"
        v-for="(item, index) in tabBar"
        :key="index"
        :class="tabBarIndex == index ? 'main-text-color' : ''"
        :id="`tab${index}`"
        @tap="handleTap(index)"
      >
        <text class="font-md ">{{ item.name }}</text>
      </view>
    </scroll-view>
    <swiper
      :duration="100"
      :current="tabBarIndex"
      :style="`height:${scrollH}px;`"
      @change="onChangeTabbar"
    >
      <swiper-item v-for="(item1, index1) in tabBar" :key="index1">
        <scroll-view scroll-y :style="`height:${scrollH}px;`" @scrolltolower="handleScorllBtm(index1)">
          <view v-for="(listitem, listindex) in item1.list" :key="listindex">
            <swiper-image v-if="listitem.type == 'swiper'" :swipers="listitem.data" />
            <template v-else-if="listitem.type == 'icons'">
              <index-nav :icons="listitem.data" />
              <divider />
            </template>
            <three-adv v-else-if="listitem.type == 'threeAdv'" :data="listitem.data" />
            <card
              v-else-if="listitem.type == 'bodyCover'"
              headTitle="每日精选"
              :bodyCover="listitem.data.bodyCover"
            ></card>
            <view
              v-else-if="listitem.type == 'list'"
              class="row j-sb"
              style="margin-bottom: 100rpx;"
            >
              <block v-for="(item, index) in listitem.data" :key="index">
                <commonList :item="item" />
              </block>
            </view>
          </view>
            <divider />
          <view class="d-flex a-center j-center text-light-muted font-md py-3">上拉加载更多</view>
        </scroll-view>
      </swiper-item>
    </swiper>
  </view>
</template>

<script>
import swiperImage from '@/components/index/swiper-image.vue';
import indexNav from '@/components/index/index-nav.vue';
import divider from '@/components/common/divider.vue';
import threeAdv from '@/components/index/three-adv.vue';
import card from '@/components/common/card.vue';

import commonList from '@/components/common/common-list.vue';
export default {
  components: {
    swiperImage,
    indexNav,
    divider,
    threeAdv,
    card,

    commonList
  },
  data() {
    return {
      scrollInto: 'tab0',
      scrollH: 500,
      tabBar: [
        {
          name: '关注',
          list: [
            {
              type: 'swiper',
              data: [
                {
                  src: '../../static/images/demo/demo4.jpg'
                }
              ]
            },
            {
              type: 'icons',
              data: [
                {
                  src: '../../static/images/indexnav/1.png'
                },
                {
                  src: '../../static/images/indexnav/2.gif'
                },
                {
                  src: '../../static/images/indexnav/3.gif'
                },
                {
                  src: '../../static/images/indexnav/4.gif'
                },
                {
                  src: '../../static/images/indexnav/5.gif'
                },
                {
                  src: '../../static/images/indexnav/6.gif'
                },
                {
                  src: '../../static/images/indexnav/7.gif'
                },
                {
                  src: '../../static/images/indexnav/8.gif'
                },
                {
                  src: '../../static/images/indexnav/9.gif'
                },
                {
                  src: '../../static/images/indexnav/10.gif'
                }
              ]
            },
            {
              type: 'threeAdv',
              data: {
                left: {
                  src: '/static/images/demo/demo1.jpg'
                },
                rightTop: {
                  src: '/static/images/demo/demo2.jpg'
                },
                rightBtm: {
                  src: '/static/images/demo/demo3.jpg'
                }
              }
            },
            {
              type: 'bodyCover',
              data: {
                bodyCover: '/static/images/demo/demo4.jpg'
              }
            },
            {
              type: 'list',
              data: [
                {
                  cover: '../../static/images/demo/list/1.jpg',
                  title: '米家空调',
                  desc: '1.5匹变频',
                  price1: '23322',
                  price2: '1199'
                },
                {
                  cover: '../../static/images/demo/list/1.jpg',
                  title: '米家空调',
                  desc: '1.5匹变频',
                  price1: '23322',
                  price2: '1199'
                },
                {
                  cover: '../../static/images/demo/list/1.jpg',
                  title: '米家空调',
                  desc: '1.5匹变频',
                  price1: '23322',
                  price2: '1199'
                },
                {
                  cover: '../../static/images/demo/list/1.jpg',
                  title: '米家空调',
                  desc: '1.5匹变频',
                  price1: '23322',
                  price2: '1199'
                }
              ]
            }
          ]
        },
        {
          name: '推荐'
        },
        {
          name: '体育'
        },
        {
          name: '热点'
        },
        {
          name: '新闻'
        },
        {
          name: '娱乐'
        },
        {
          name: '推荐1'
        },
        {
          name: '体育1'
        },
        {
          name: '热点1'
        },
        {
          name: '新闻1'
        },
        {
          name: '娱乐1'
        }
      ],
      tabBarIndex: 0
    };
  },
  onLoad() {
    uni.getSystemInfo({
      success: res => {
        this.scrollH = res.windowHeight - uni.upx2px(80);
      }
    });
    this.init()
  },
  methods: {
    init(){},
    handleTap(index) {
      this.tabBarIndex = index;
      this.scrollInto = `tab${index}`;
    },
    onChangeTabbar(val) {
      const index = val.detail.current;
      this.tabBarIndex = index;
      this.scrollInto = `tab${index}`;
    },
    handleScorllBtm(index){
      console.log('上拉加载更多触发')
    }
  }
};
</script>

<style lang="scss">
.content {
  overflow-x: hidden;
  overflow-y: auto;
}
</style>
