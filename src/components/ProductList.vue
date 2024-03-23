<template>
  <div>
    <button class="logout primary" @click="logout">LOGOUT</button>
    <h2 class="title">Suzuki Motorcycles</h2>
    <ul class="product-list">
      <li v-for="product in products" :key="product.id" class="product-item">
        <span class="product-name">{{ product.name }}</span>
        <span class="product-price">₱{{ product.price }}</span>
        <button @click="addToCart(product)" class="add-to-cart-btn primary">Add to Cart</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ProductList',
  props: {
    products: Array,
    addToCart: Function
  },
  methods: {
    logout() {
      localStorage.removeItem('token')
      this.$router.push('/login')
    }
  }
}
</script>

<style scoped>
.title {
  font-size: 24px;
  color: #000000; 
  text-align: center;
  margin-bottom: 20px;
}

.product-list {
  list-style: none;
  padding: 0;
}

.product-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 10px;
  border-bottom: 1px solid #4a90e2;
  border-left: 1px solid #4a90e2;
}

.product-name {
  flex: 1;
  color: #000000;
}

.product-price {
  margin-right: 20px;
  color: #000000;
}

.add-to-cart-btn {
  background-color: #4a90e2; 
  color: #ffffff; 
  border: none;
  padding: 8px 12px;
  border-radius: 5px;
  cursor: pointer;
}

.logout {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: #4a90e2;
  color: #ffffff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}

</style>
