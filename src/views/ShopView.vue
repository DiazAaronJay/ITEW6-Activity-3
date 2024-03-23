<template>
  <div class="shop">
    <div class="container product-container">
      <h2 class="section-title"></h2>
      <ProductList :products="products" :addToCart="addToCart" />
    </div>
    <div class="container cart-container">
      <h2 class="section-title"></h2>
      <Cart :cart="cart" :removeFromCart="removeFromCart" :updateQuantity="updateQuantity" />
    </div>
  </div>
</template>

<script>
import ProductList from '@/components/ProductList.vue';
import Cart from '@/components/Cart.vue';

export default {
  name: 'ShopView',
  components: {
    ProductList,
    Cart
  },
  data() {
    return {
      products: [
        { id: 1, name: 'Suzuki GSX-R1000', price: 15000 },
        { id: 2, name: 'Suzuki Hayabusa GSX1300R', price: 18000 },
        { id: 3, name: 'Suzuki V-Strom 650', price: 10000 },
        { id: 4, name: 'Suzuki Burgman 650', price: 11000 },
        { id: 5, name: 'Suzuki GSX250R', price: 6000 },
        { id: 6, name: 'Suzuki Raider FI', price: 12000 },
        { id: 7, name: 'Honda CBR1000RR', price: 16000 },
        { id: 8, name: 'Honda Gold Wing', price: 25000 },
        { id: 9, name: 'Honda CRF450R', price: 9800 },
        { id: 10, name: 'Honda CB650R', price: 9000 },
        { id: 11, name: 'Honda Alpha Wave (Old)', price: 2000 }
      ],
      cart: []
    }
  },
  methods: {
    addToCart(product) {
      if(localStorage.getItem('token')) {
        const index = this.cart.findIndex(item => item.id === product.id);
        if (index !== -1) {
          this.cart[index].quantity++;
        } else {
          this.cart.push({ ...product, quantity: 1 });
        }
      } else {
        alert('You are not logged in.');
        this.$router.push('/login');
      }
    },
    removeFromCart(index) {
      this.cart.splice(index, 1);
    },
    updateQuantity(index, newQuantity) {
      if (newQuantity < 1) {
        newQuantity = 1;
      }
      this.cart[index].quantity = parseInt(newQuantity);
    }
  }
}
</script>

<style scoped>
.shop {
  display: flex;
  background-color: #e9f1f7; 
}

.container {
  flex: 1;
  padding: 20px;
  border-radius: 10px;
  background-color: #ffffff;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  margin: 10px;
}

.section-title {
  margin-top: 0;
  margin-bottom: 20px;
  font-size: 24px;
  color: #333333; 
}

.product-container {
  width: 70%;
}

.cart-container {
  width: 30%;
}
</style>
