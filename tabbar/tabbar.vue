<template>
  <div>
    <div class="tabbar" @click.stop="handleTabbar">
      <div class="tab-bar-border"></div>
      <div class="tab-bar-item index" data-index="1">
        <cover-image data-index="1" :src="selectedTabbar === 1 ? '/static/tabs/home-active.jpg' : '/static/tabs/home.jpg'" class="_cover-image">
        </cover-image>
        <cover-view data-index="1" :style="{color: selectedTabbar === 1 ? selectedColor : color}">首页</cover-view>
      </div>
      <div class="tab-bar-item editText" data-index="2">
        <cover-view data-index="2" :style="{color: selectedTabbar === 2 ? selectedColor : color}">编辑</cover-view>
      </div>
      <div class="tab-bar-item my" data-index="3">
        <cover-image data-index="3" :src="selectedTabbar === 3 ? '/static/tabs/my-active.jpg' : '/static/tabs/my.jpg'" class="_cover-image">
        </cover-image>
        <cover-view data-index="3" :style="{color: selectedTabbar === 3 ? selectedColor : color}">我的</cover-view>
      </div>
    </div>
    <div class="edit" data-index="2">
      <cover-image data-index="2" :src="selectedTabbar === 2 ? '/static/tabs/edit-active.jpg' : '/static/tabs/edit.jpg'" class="_cover-image">
      </cover-image>
    </div>
  </div>
</template>
<script>
  export default {
    props: [ 'selectedTabbar' ],
    data () {
      return {
        color: '#7A7E83',
        selectedColor: '#2a7ffb'
      }
    },
    created () {
    },
    updated () {
      // console.log(this.selectedTabbar)
    },
    mounted () {
    },
    methods: {
      handleTabbar (e) {
        this.selectedTabbar = parseInt(e.target.dataset.index)
        this.$emit('selectTab', this.selectedTabbar)
        if (this.selectedTabbar === 1) {
          wx.switchTab({
            url: '/pages/index/main'
          })
        } else if (this.selectedTabbar === 2) {
          wx.switchTab({
            url: '/pages/edit/main'
          })
        } else if (this.selectedTabbar === 3) {
          wx.switchTab({
            url: '/pages/my/main'
          })
        }
      }
    },
    computed: {
    }
  }
</script>
<style scoped lang="less">
.tabbar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 48px;
  background: white;
  // display: flex;
  // padding-bottom: env(safe-area-inset-bottom);
}
.tab-bar-border {
  background-color: rgba(0, 0, 0, 0.33);
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 1px;
  transform: scaleY(0.5);
}

// .tab-bar-item {
//   flex: 1;
//   text-align: center;
//   display: flex;
//   justify-content: center;
//   align-items: center;
//   flex-direction: column;
// }
.index {
  position: absolute;
  // top: 15rpx;
  width: 50rpx;
  height: 100rpx;
  padding: 15rpx 100rpx;
}
.tab-bar-item cover-image {
  width: 40rpx;
  height: 40rpx;
}

.tab-bar-item cover-view {
  margin-top: 8rpx;
  font-size: 10px;
}
.editText {
  position: absolute;
  left: 258rpx;
  padding: 50rpx 100rpx;
}
.my {
  position: absolute;
  width: 50rpx;
  left: 500rpx;
  padding: 15rpx 100rpx;
}
.edit {
  position: fixed;
  width: 90rpx;
  height: 90rpx;
  left: 320rpx;
  bottom: 40rpx;
  padding: 10rpx;
  background: #fff;
  border: 1rpx solid #fff;
  border-radius: 50%;
}
</style>