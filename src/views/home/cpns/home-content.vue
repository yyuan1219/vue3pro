<template>
    <div class="content">
        <h2 class="title">热门精选</h2>
        <div class="list">
            <template v-for="(item, index) in houselist" :key="item.data.houseId">
                <houseItemV9 v-if="item.discoveryContentType === 9" :item-data="item.data"></houseItemV9>
                <houseItemV3 v-else-if="item.discoveryContentType === 3"
                :item-data="item.data"></houseItemV3>
            </template>
        </div>
    </div>
</template>
  
<script setup>
import houseItemV9 from "@/components/house-item-v3/index.vue"
import houseItemV3 from "@/components/house-item-v9/index.vue"
import useHomeStore from '@/stores/modules/home';
import { storeToRefs } from 'pinia';

const homeStore = useHomeStore()
const { houselist } = storeToRefs(homeStore)
</script>
  
<style lang="less" scoped>
.content {
  padding: 10px 8px;

  .title {
    font-size: 22px;
    padding: 10px;
  }

  .list {
    display: flex;
    flex-wrap: wrap;
  }
}
</style>