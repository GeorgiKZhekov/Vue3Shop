<template>
  <header class="top-bar spread">
      <nav class="top-bar-nav">
        <RouterLink to="/" class="top-bar-link">
          <i class="icofont-spoon-and-fork"></i>
          <span>Home</span>
        </RouterLink>
        <RouterLink to="/products" class="top-bar-link">
          <span>Products</span>
        </RouterLink>
        <RouterLink to="/pastOrders" class="top-bar-link">
          <span>Past Orders</span>
        </RouterLink>
      </nav>
      <div @click="toggleSidebar" class="top-bar-cart-link">
        <i class="icofont-cart-alt icofont-1x"></i>
        <span>Cart ({{totalQty}})</span>
      </div>
    </header>
<RouterView :inventory = "inventory" :addToCart = "addToCart"/>

<Sidebar
  v-if="showSidebar" 
  :toggle="toggleSidebar"
  :cart="cart"
  :inventory="inventory"
  :remove="removeItem" />
</template>


<script setup>
  import Sidebar from './components/SidebarComponent.vue'
  import { ref, computed } from 'vue'
  import food from './food.json'

  let showSidebar = ref(false);
  const inventory = ref(food);
  let cart = ref({});

  const totalQty = computed(() => Object.values(cart.value).reduce((acc, curr) => acc + curr, 0));
  
  function addToCart(name, index) {
    if(inventory.value[index].quantity !== 0){
      if(!cart.value[name]) cart.value[name] = 0;
      cart.value[name] += inventory.value[index].quantity;
      inventory.value[index].quantity = 0;
    }
  }

  function toggleSidebar() {
    showSidebar.value = !showSidebar.value;
  }

  function removeItem(name) {
    delete cart.value[name];
  }
</script>



