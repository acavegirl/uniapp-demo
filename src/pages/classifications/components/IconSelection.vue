<template>
	<view>
		<swiper :indicator-dots="true" class="swiper">
      <swiper-item v-for="data in swiperData">
				<uv-grid :col="5" :border="false" align="center" class="swiper-item" @click="click">
					<uv-grid-item
            :name="item"
						v-for="(item, index) in data" 
						:index="index" 
						:key="index">
						<uv-icon :customStyle="{paddingTop:20+'rpx'}" :name="item.icon" :size="22"></uv-icon>
						<text class="grid-text">{{item.text}}</text>
					</uv-grid-item>
				</uv-grid>
			</swiper-item>
		</swiper>
	</view>
</template>
<script>
export default {
  data() {
    return {
      swiperData: [
        [
          {text: '外卖', icon: 'integral'},
          {text: '美食', icon: 'email'},
          {text: '酒店/民宿', icon: 'coupon'},
          {text: '休闲玩乐', icon: 'gift'},
          {text: '电影/演出', icon: 'scan'},
          {text: '打车', icon: 'pause-circle'},
          {text: '小象超市', icon: 'pause-circle'},
          {text: '骑车', icon: 'pause-circle'},
          {text: '看病买药', icon: 'pause-circle'},
          {text: '超市便利', icon: 'pause-circle'},
        ],
        [
          {text: '特价团', icon: 'integral'},
          {text: '景点/门票', icon: 'email'},
          {text: '免费领鸡蛋', icon: 'coupon'},
          {text: '拼好饭', icon: 'gift'},
          {text: '蔬菜水果', icon: 'scan'},
          {text: '跑腿', icon: 'volume-off'},
          {text: 'KTV', icon: 'volume-off'},
          {text: '买酒', icon: 'volume-off'},
          {text: '汽车票', icon: 'volume-off'},
          {text: '宠物', icon: 'volume-off'},
        ],
        [
          {text: '养车/用车', icon: 'integral'},
          {text: '丽人/美发', icon: 'email'},
          {text: '火车/机票', icon: 'coupon'},
          {text: '生活服务', icon: 'gift'},
          {text: '品质百货', icon: 'scan'},
          {text: '医疗/口腔', icon: 'list'},
          {text: '游泳/健身', icon: 'list'},
          {text: '学习培训', icon: 'list'},
          {text: '周边游', icon: 'list'},
          {text: '充电宝', icon: 'list'},
        ]
      ]
    }
  },
  methods: {
    click(item) {
      uni.showToast({
        icon: 'none',
        title: item.text
      })
    }
  }
}
</script>
<style lang="scss">
	.swiper {
		height: 300rpx;
    // margin-bottom: 20rpx;
	}
  // .uni-swiper-dots {
  //   margin-top: 20rpx;
  // }
	.grid-text {
		font-size: 14px;
		color: #909399;
		padding: 10rpx 0 20rpx 0rpx;
		/* #ifndef APP-PLUS */
		box-sizing: border-box;
		/* #endif */
	}
</style>