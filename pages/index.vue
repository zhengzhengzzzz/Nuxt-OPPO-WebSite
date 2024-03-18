<template>
  <div class="home">
    <div class="wrapper content">
      <swiper :banners="banners"></swiper>
      <tab-category :categorys="categorys" @item-click="handleItemClick"></tab-category>
      <template v-for="category in categorys" :key="category.id">
        <section-category :category="category"></section-category>
      </template>
    </div>
  </div>
</template>
<script lang="ts" setup>
import { ElButton } from 'element-plus';
import { storeToRefs } from 'pinia';
import { ICategory, useHomeStore } from '~~/store/home';
interface IProps {
  title: string
}
const props = withDefaults(defineProps<IProps>(), {
  title: "AA",
})
const homeStore = useHomeStore()
const { banners, categorys } = storeToRefs(homeStore)

function handleItemClick(item: ICategory) {
  //进行页面跳转 编程导航 不利于seo
  return navigateTo({
    path: '/oppo-detail',
    query: {
      type: item.type
    }
  })
}
</script>
<style lang="scss" scoped>
.home {
  background-color: $bgGrayColor;
}
</style>