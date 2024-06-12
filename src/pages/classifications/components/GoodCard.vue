<template>
  <view style="background-color: #fff" class="border-rd-sm">

    <view id="img">
      <image :src="props.img" :style="`width: ${width}`" mode="widthFix"></image>
    </view>

    <view class="pl-2 pr-2 pb-2">
      <view id="text" class="text-size-sm">
        {{ props.text }}
      </view>
      <view id="subtext" v-if="props.subtext" class="flex text-size-xs color-#9ca3af">
        <view>{{ props.subtext[0] }}</view>
        <view v-if="props.subtext[1]" class="flex grid-items-center">
          <uv-line direction="col" length="70%" hairline="false" color="#9ca3af" margin="0rpx 8rpx"></uv-line>
          <view>{{ props.subtext[1] }}</view>
        </view>
      </view>
      <view id="subtext-highlight" v-if="props.subtextHighlight" class="flex text-size-xs color-#dc2626">
        <view>{{ `经典必吃: ${props.subtextHighlight.join(' ')}`}}</view>
      </view>

      <view class="flex grid-items-center">
        <view id="price" v-if="props.price" class="mr-2">
          <span class="font-700 color-#dc2626 mr-1"><span class="text-size-xs">￥</span><span class="text-size-sm">{{ props.price.new }}</span></span>
          <span class="text-size-xs decoration-line-through">￥{{ props.price.old }}</span>
        </view>
        <view id="tags" v-if="props.tags" class="flex">
          <view v-for="item in props.tags" plain type="error" style="font-size: 0.6rem !important; padding-top: 0.1rem" class="color-#dc2626 border-1 border-rd-md border-color-#dc2626 pr-1 pl-1 mr-1">
            <view>{{item}}</view>
          </view>
        </view>
      </view>
      
      <view
        id="link"
        v-if="props.link"
        class="flex grid-items-center border-rd-lg pl-2 pr-1 float"
        style="background-color: #f4f4f5;"
        @click="onclick"
      >
        <image :src="props.link.icon" class="mr-1" style="width: 0.8rem; height: 0.8rem"></image>
        <view style="font-size: 0.6rem; padding-top: 0.1rem">{{ props.link.text }}</view>
        <uv-icon name="arrow-right" size="10" style="margin-left: auto"></uv-icon>
      </view>
    </view>
    
  </view>
</template>

<script setup>
import { ref, computed } from 'vue'
import { getCurrentInstance } from "vue";
const { appContext } = getCurrentInstance();

const props = defineProps(['title', 'text', 'img', 'subtext', 'subtext-highlight', 'price', 'tags', 'link', 'leftGap', 'rightGap', 'columnGap'])

const width = ref('0px')

uni.getSystemInfo({
  success: function (res) {
    width.value = (res.windowWidth - props.leftGap - props.rightGap - props.columnGap)/2 + 'px';
  }
});

const onclick = ()=> {
  appContext.config.globalProperties.$Router.push({
    path: '/example',
  })
}

</script>

<style scoped lang="scss">
$show-lines: 1;
@import '@climblee/uv-ui/libs/css/variable.scss';
.waterfall-item {
  overflow: hidden;
  margin-top: 10px;
  border-radius: 6px;
}
.waterfall-item__ft {
  padding: 20rpx;
  background: #fff;
  &__title {
    margin-bottom: 10rpx;
    line-height: 48rpx;
    font-weight: 700;
    .value {
      font-size: 32rpx;
      color: #303133;
    }
  }
  &__desc .value {
    font-size: 28rpx;
    color: #606266;
  }
  &__btn {
    padding: 10px 0;
  }
}
</style>