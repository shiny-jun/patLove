<template>
    <div class="current">
        <div class="scroll">
            <scroll-view class="scroll-view_H" scroll-x style="width: 100%">
                <view v-for="(type,index) in types" :key="index" class="scroll-item" :style="{color:currentTab==index?'#000000':'#999999'}" @click="changeCurrentTab(index)">{{type.name}}</view>
            </scroll-view>
        </div>
        <div class="swiper">
            <swiper autoplay="false" :current="currentTab">
                <block v-for="(type,index) in types" :key="index">
                    <swiper-item>
                        <slot :name='type.value'></slot>
                    </swiper-item>
                </block>
            </swiper>
        </div>
    </div>
</template>
<script>
export default {
    props: ['types'],
  data() {
    return {
      currentTab:0
    };
  },methods: {
      changeCurrentTab(index){
          this.currentTab = index
      },
      bindchangeCurrent(e){
          console.log(e.detail.current)
          this.currentTab = e.detail.current
      }
  },
};
</script>
<style lang="scss" scoped>
.current{
    height: calc(100vh - 80rpx);

    .scroll{
        width: 100%;
        height: 60rpx;
        line-height: 60rpx;
        scroll-view{
            white-space: nowrap;
        }
        .scroll-item{
            color: #999999;
            font-size: 28rpx;
            display: inline-block;
            padding: 0 40rpx;
        }
    }
}
</style>
