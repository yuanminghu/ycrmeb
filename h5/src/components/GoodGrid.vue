<template>
  <div class="productList" ref="container">
    <div
      style="margin-top: 0"
      class="list acea-row row-between-wrapper"
      :class="Switch === true ? '' : 'on'"
      ref="container"
    >
      <div
        @click="goDetail(item)"
        v-for="(item, index) in goodList"
        :key="index"
        class="item"
        :class="Switch === true ? '' : 'on'"
        :title="item.store_name"
      >
        <div class="pictrue" :class="Switch === true ? '' : 'on'">
          <img :src="item.image" :class="Switch === true ? '' : 'on'" />
          <span
            class="pictrue_log_class"
            :class="Switch === true ? 'pictrue_log_big' : 'pictrue_log'"
            v-if="item.activity && item.activity.type === '1'"
          >秒杀</span>
          <span
            class="pictrue_log_class"
            :class="Switch === true ? 'pictrue_log_big' : 'pictrue_log'"
            v-if="item.activity && item.activity.type === '2'"
          >砍价</span>
          <span
            class="pictrue_log_class"
            :class="Switch === true ? 'pictrue_log_big' : 'pictrue_log'"
            v-if="item.activity && item.activity.type === '3'"
          >拼团</span>
        </div>
        <div class="text" :class="Switch === true ? '' : 'on'">
          <div class="name line1">{{ item.store_name }}</div>
          <div class="money font-color-red" :class="Switch === true ? '' : 'on'">
            ￥
            <span class="num">{{ item.price }}</span>
          </div>
          <div class="vip acea-row row-between-wrapper" :class="Switch === true ? '' : 'on'">
            <div class="vip-money" v-if="item.vip_price && item.vip_price > 0">
              ￥{{ item.vip_price }}
              <img src="@assets/images/vip.png" />
            </div>
            <div>已售{{ item.sales }}件</div>
          </div>
        </div>
      </div>
      
    </div>
  </div>
</template>
<script>
import { goShopDetail } from "@libs/order";
export default {
  name: "GoodGrid",
  props: {
    goodList: {
      type: Array,
      default: () => []
    },
    isSort: {
      type: Boolean,
      default: true
    }
  },
  data: function() {
    return {
      Switch: true
    };
  },
  methods: {
    // 商品详情跳转
    goDetail(item) {
      goShopDetail(item).then(() => {
        this.$router.push({ path: "/detail/" + item.id });
      });
    },
    test() {
      console.log(this.goodsList);
    }
  }
};
</script>
