<template>
    <div class="search-bar">
       <div class="bar" v-if="!canuse">
           <div class="bar-wrapper" @click="goSearchPage">
               <i class="iconfont icon-search"></i>
               <input class="input" type="text" disabled>
               <!-- <i class="iconfont icon-del2"></i> -->
           </div>
       </div>
       <div class="bar flex" v-else>
           <div class="bar-wrapper">
               <i class="iconfont icon-search"></i>
               <input class="input" v-model="inpVal" type="text" @blur="handleInput">
               <i class="iconfont icon-del2" v-if="inpVal"></i>
           </div>
           <div class="close" @click="handleInput">搜索</div> 
       </div>
    </div>
</template>
<script>
export default {
  props: ["canuse"],
  data() {
    return {
      inpVal: ""
    };
  },
  methods: {
    goSearchPage() {
      wx.navigateTo({
        //前往搜索页
        url: "/pages/searchPage/main"
      });
    },
    handleInput(val) {
      this.$emit("handleInput", val.target.value);
    }
  }
};
</script>
<style lang="scss" scoped>
.search-bar {
  width: 100%;
  box-shadow:0px 0px 2px 0px rgba(65,47,141,0.2);
  // height: 80rpx;
  .bar {
    width: 100%;
    height: 100%;
    padding: 10rpx 0;
    .bar-wrapper {
      position: relative;
      margin: 0 10rpx;
      height: 60rpx;
      line-height: 60rpx;
      background-color: #f0f0f0;
      border-radius: 30rpx;
      .input {
        height: 40rpx;
        line-height: 40rpx;
        vertical-align: middle;
        margin: auto 70rpx;
        padding-top: 8rpx;
      }
      .icon-search {
        position: absolute;
        color: #a5a5a5;
        font-size: 36rpx;
        left: 20rpx;
      }
      .icon-del2 {
        position: absolute;
        color: #bebebe;
        font-size: 28rpx;
        top: 0;
        right: 20rpx;
      }
    }
    .close {
      height: 100%;
      font-size: 28rpx;
      padding: 0 10rpx;
      margin-right: 10rpx;
    }
  }
  .flex {
    display: flex;
    align-items: center;
    .bar-wrapper {
      flex: 1;
    }
  }
}
</style>
