<template>
  <div class="menu">
    <div class="menuTitle">智慧大棚</div>
    <div class="menuTxt">智慧农业信息化管理平台</div>
    <ul class="menuUl">
      <li class="menuLi" @click="goGreenhouse()">
        <div class="menuLi-img"
          :style="{
            'background':'rgba(255,246,234,1)',
            'height':'73rpx',
            'padding-top':'35rpx'
          }"
        >
          <img src="../../../static/images/greenhouse.png" :style="{'width':'44rpx','height':'36rpx'}">
        </div>
        <div class="menuLi-txt">数据分析</div>
      </li>
      <li class="menuLi" @click="goRealtimedata()">
        <div class="menuLi-img"
          :style="{
            'background':'rgba(230,255,251,1)',
            'height':'75rpx',
            'padding-top':'33rpx'
          }"
        >
          <img src="../../../static/images/realtimedata.png" :style="{'width':'51rpx','height':'45rpx'}">
        </div>
        <div class="menuLi-txt">实时数据</div>
      </li>
      <li class="menuLi" @click="goControl()">
        <div class="menuLi-img"
          :style="{
            'background':'rgba(240,241,254,1)',
            'height':'74rpx',
            'padding-top':'34rpx'
          }"
        >
          <img src="../../../static/images/control.png" :style="{'width':'41rpx','height':'41rpx'}">
        </div>
        <div class="menuLi-txt">设备控制</div>
      </li>
      <li class="menuLi" @click="goAutomatic()">
        <div class="menuLi-img"
          :style="{
            'background':'rgba(255,240,236,1)',
            'height':'76rpx',
            'padding-top':'32rpx'
          }"
        >
          <img src="../../../static/images/automatic.png" :style="{'width':'45rpx','height':'45rpx'}">
        </div>
        <div class="menuLi-txt">自动控制</div>
      </li>
      <li class="menuLi" @click="goTiming()">
        <div class="menuLi-img"
          :style="{
            'background':'rgba(228,242,253,1)',
            'height':'79rpx',
            'padding-top':'29rpx'
          }"
        >
          <img src="../../../static/images/timing.png" :style="{'width':'45rpx','height':'51rpx'}">
        </div>
        <div class="menuLi-txt">定时任务</div>
      </li>
      <li class="menuLi" @click="goVideo()">
        <div class="menuLi-img"
          :style="{
            'background':'rgba(255,246,234,1)',
            'height':'80rpx',
            'padding-top':'28rpx'
          }"
        >
          <img src="../../../static/images/video.png" :style="{'width':'42rpx','height':'52rpx'}">
        </div>
        <div class="menuLi-txt">视频监控</div>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  data () {
    return {
      projectId: ''
    }
  },
  created:function(){
    wx.hideShareMenu();//禁止出现转发按钮
    this.getHeight();
  },
  mounted() {
    this.projectId = wx.getStorageSync('projectId')
  },
  methods: {
    //跳转数据分析页
    goGreenhouse(){
      wx.navigateTo({
        url: `/pages/sub/greenhouse/main`,
      })
    },
    //跳转实时数据页
    goRealtimedata(){
      wx.navigateTo({
        url: `/pages/realtimedata/main`,
      })
    },
    //跳转设备控制页
    goControl(){
      wx.navigateTo({
        url: `/pages/control/main`,
      })
    },
    //跳转自动控制页
    goAutomatic(){
      wx.navigateTo({
        url: `/pages/automatic/main`,
      })
    },
    //跳转定时任务页
    goTiming(){
      wx.navigateTo({
        url: `/pages/timing/main`,
      })
    },
    //跳转视频监控页
    goVideo(){
      wx.navigateTo({
        url: `/pages/sub/videoList/main`,
      })
    },
    /**测量屏幕高度,计算标题栏高度 */
    getHeight(){
      let that = this;
      wx.getSystemInfo({
        success: function(res) {
          that.navH = res.statusBarHeight + 46;
          that.$httpWX.setStorage("navH",that.navH);
          // that.$store.commit('setnavH',that.navH);
        }
      })
    },
  }
}
</script>

<style scoped>
.menu{
  padding: 20rpx 50rpx 0;
  background: #F3F5F8;
  height: 100vh;
  overflow: hidden;
}
.menuTitle{
  padding-top: 64rpx;
  font-size:23px;
  font-family:PingFang SC;
  font-weight:bold;
  color:rgba(17,17,17,1);
}
.menuTxt{
  padding-top: 38rpx;
  font-size:14px;
  font-family:PingFang SC;
  font-weight:400;
  color:rgba(153,153,153,1);
}
.menuUl{
  padding-top: 60rpx;
  width: 650rpx;
  height: 1078rpx;
  display: flex;
  justify-content: space-between;
  flex-wrap:wrap;
}
.menuLi{
  width:299rpx;
  height:253rpx;
  padding-top: 60rpx;
  background:rgba(255,255,255,1);
  box-shadow:0px 5px 15px 0px rgba(167,197,242,0.3);
  border-radius:18px;
  text-align: center;
  margin-bottom: 20px;
}
.menuLi-img{
  width: 108rpx;
  margin:0 auto;
  border-radius: 50%;
  text-align: center;
}
.menuLi-txt{
  padding-top: 53rpx;
  font-size:34rpx;
  font-family:PingFang SC;
  font-weight:500;
  color:rgba(15,61,168,1);
}
</style>
