<template>
    <div class="grid-view-item">
        <div class="item-img">
            <img class="url" :src="productDetailss.url" alt="">
        </div>
        <div class="item-title">{{ productDetailss.title }}</div>
        <div class="item-labels">
            <span class="label" v-for="item in productDetailss.activityList">
                {{ item.activityInfo }}
            </span>
        </div>
        <div class="item-price">
            <span class="prefix">{{ productDetailss.priceInfo?.prefix }}</span>
            <span class="prefix">{{ productDetailss.priceInfo?.currencyTag }}</span>
            <span class="price">{{ productDetailss.priceInfo?.buyPrice }}</span>
        </div>
    </div>
</template>
<script lang="ts" setup>
import { IProductDetail } from "~~/store/home"

interface IProps {
    productDetailss: IProductDetail
}
const props = withDefaults(defineProps<IProps>(), {
    productDetailss: () => ({}),
})
</script>
<style lang="scss" scoped>
.grid-view-item {
    text-align: center;
    background-color: #fff;
    border-radius: 8px;
    transition: all 0.2s linear;

    &:hover {
        @include hoverEffect();
    }

    .item-img {
        .url {
            width: $imgWidth;
            height: $imgHeight;
            margin-top: 14px;
            margin-bottom: 7px;
        }
    }

    .item-title {
        padding: 0 20px;
        margin-top: 2px;
        font-weight: 500;
        font-size: 15px;
        text-align: center;
        @include textEllipsis();
    }

    .item-labels {
        height: 45px;
        display: flex;
        justify-content: center;
        align-items: center;

        .label {
            display: inline-block;
            padding: 1px 2px;
            color: $priceColor;
            font-size: 13px;
            border: 1px solid $priceColor;
            margin-right: 4px;
            margin-bottom: 4px;
        }
    }

    .item-price {
        padding-bottom: 40px;

        .prefix {
            color: $priceColor;
            font-size: 13px;
        }

        .price {
            color: $priceColor;
            font-size: 20px;
            line-height: 1;
        }
    }
}
</style>