<template>
    <div class="card">
        <div class="card-title">
          {{product.name}}
        </div>
        <div class="card-body">
          <i class="icofont-10x icofont-{{product.icon}}"></i>
          <form>
            <div class="row">
              <div class="cell">
                <label>Type:</label>
              </div>
              <div class="cell">
                <em>{{product.type}}</em>
              </div>
            </div>
            <div class="row">
              <div class="cell">
                <label>Price:</label>
              </div>
              <div class="cell">
                ${{ product.price.USD }}
              </div>
            </div>
            <div class="row">
              <div class="cell">
                <label>Quantity:</label>
              </div>
              <div class="cell">
                <!-- The ".quantity" property is added to the object when needed. Look at vue dev tools -->
                <input type="number" v-model.number="product.quantity">
              </div>
            </div>
          </form> 
        </div>
        <div class="card-footer">
          <button v-on:click="addToCart(product.name, index)" class="btn btn-light">
            Add to cart
          </button>
        </div>
      </div>
</template>

<script setup>
  defineProps(['product', 'index', 'addToCart']);
  
</script>