<template>
  <div class="onePlus">
    <div class="wrapper content">
      <swiper :banners="banners"></swiper>
      <tab-category :categorys="categorys"></tab-category>
      <template v-for="category in categorys" :key="category.id">
        <section-category :category="category"
          v-if="category.productDetailss && category.productDetailss?.length"></section-category>
      </template>
    </div>
  </div>
</template>
<script lang="ts" setup>
import { getHomeInfo } from "~~/service/home";

const { data } = await getHomeInfo('onePlus')
const { banners, categorys } = data.value!.data
</script>

<style lang="scss" scoped>
.one-plus {
  background-color: $bgGrayColor;
}
</style>
