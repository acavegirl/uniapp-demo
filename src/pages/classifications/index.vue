<template>
  <view class="bg-yellow">
    <view class="flex">
      <uv-input placeholder="后置插槽" class="flex-auto">
        <!-- vue3模式下必须使用v-slot:suffix -->
        <template v-slot:suffix>
          <uv-button
            @click="getCode"
            text="搜索"
            type="success"
            size="mini"
          ></uv-button>
        </template>
      </uv-input>
      <view class="m-2 flex-none">
        <uni-icons type="scan" size="30"></uni-icons>
      </view>
    </view>
  </view>
  
  <view>
    <IconSelection />
  </view>

  <view class="bg-yellow">
    <view class="flex" style="height: 5rem">
      
    </view>
  </view>

  <view style="background-color: #f4f4f5; padding-bottom: 4rem">
    <RecommendedGoods />
  </view>
</template>

<script>
import RecommendedGoods from './components/RecommendedGoods.vue';
import IconSelection from './components/IconSelection.vue';

export default {
  components: {
    RecommendedGoods,
    IconSelection,
  },
  data() {
    return {
    }
  },
  methods: {
  },
  onLoad(params) {
    console.log('params', params)
  },
}
</script>

<style></style>