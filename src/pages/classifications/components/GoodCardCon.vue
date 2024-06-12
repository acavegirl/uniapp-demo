<template>
  <view id="title" v-if="props.title">
    <span>{{ props.title.text }}</span>
    <uv-tags :text="props.title.tag" type="error" shape="circle" size="mini"></uv-tags>
  </view>
</template>