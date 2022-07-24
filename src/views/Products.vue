<template>
  <ProductsList v-for="product in items" :key="product.id" :product="product" />
</template>

<script>
import ProductsList from '@/components/ProductsList.vue';
import items from '@/data/items.js';

export default {
  components: {
    ProductsList,
  },
  data() {
    return {
      items: items,
      message: '',
    };
  },
};
</script>
