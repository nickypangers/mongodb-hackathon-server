<template>
  <div class="border rounded-xl p-3">
    <p><span class="font-bold">Order ID:</span> {{ order._id }}</p>
    <p>
      <span class="font-bold">Order Date:</span>
      {{ new Date(order.created_at) }}
    </p>
    <p><span class="font-bold">Name:</span> {{ order.customer_name }}</p>
    <p><span class="font-bold">Email:</span> {{ order.customer_email }}</p>
    <p class="font-bold">Shopping Bag:</p>
    <order-result-cart-item
      v-for="product in order.cart"
      :product="product"
      :key="product._id"
    />
    <p class="mt-3">
      <span class="font-bold">Total:</span> {{ formatPrice(order.total_price) }}
    </p>
  </div>
</template>
<script>
import global from '~/mixins/global'
export default {
  name: 'OrderResult',
  props: {
    order: {
      type: Object,
      default: () => {},
    },
  },
  mixins: [global],
  data() {
    return {}
  },
}
</script>
<style lang="scss" scoped>
p {
  @apply pb-1;
}
</style>
