<template>
  <div>
    <h2 class="title">Shopping Cart</h2>
    <table class="cart-table">
      <thead>
        <tr>
          <th>Product</th>
          <th>Quantity</th>
          <th>Price</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in cart" :key="item.id" class="cart-item">
          <td>{{ item.name }}</td>
          <td>
            <input type="number" v-model="item.quantity" min="1" @input="updateQuantity(index, $event.target.value)" class="quantity-input">
          </td>
          <td>₱{{ item.price * item.quantity }}</td>
          <td>
            <button @click="removeFromCart(index)" class="remove-btn primary">Remove</button>
          </td>
        </tr>
      </tbody>
    </table>
    <p class="total">Total: ₱{{ total }}</p>
  </div>
</template>

<script>
export default {
  name: 'ShoppingCart',
  props: {
    cart: Array,
    removeFromCart: Function,
    updateQuantity: Function
  },
  computed: {
    total() {
      return this.cart.reduce((total, item) => total + (item.price * item.quantity), 0);
    }
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

.cart-table {
  width: 100%;
  border-collapse: collapse;
}

.cart-table th,
.cart-table td {
  border: 1px solid #4a90e2;
  padding: 8px;
  text-align: left;
}

.cart-table th {
  background-color: #4a90e2; 
  color: #ffffff; 
}

.quantity-input {
  width: 50px;
}

.remove-btn {
  background-color: #ffffff;
  color: #4a90e2;
  border: none;
  padding: 8px 12px;
  border-radius: 5px;
  cursor: pointer;
}

.remove-btn:hover {
  background-color: #4a90e2; 
  color: #f0f0f0;
}

.total {
  font-size: 18px;
  font-weight: bold;
  color: #4a90e2; 
  text-align: center;
}
</style>
