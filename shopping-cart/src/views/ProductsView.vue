<template>
  <main class="wrapper">
    <h1>Products</h1>
    <div class="card-container">
      <ProductCard 
        v-for="(product, index) in inventory" 
        :key="product.id" 
        :index="index"
        :product="product"
        :addToCart="addToCart"
        class="card"/>
    </div>
  </main>
</template>

<script setup>
  import ProductCard from '@/components/ProductCardComponent.vue'

  const props = defineProps(['inventory', 'addToCart']);
</script>