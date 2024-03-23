<template>
  <div class="app-container">
    <div class="product-container">
      <h2>Available Flowers</h2>
      <ul>
        <li v-for="f in flowers" :key="f.id" class="flower-card">
          <div class="flower-info">
            <span>{{ f.name }}</span>
            <span>₱{{ f.price | formatPrice }}</span>
          </div>
          <div class="flower-actions">
            <button @click="buy(f)" :disabled="!isLoggedIn">Buy Now</button>
          </div>
        </li>
      </ul>
    </div>

    <div class="cart-container">
      <h2>Your Cart</h2>
      <ul>
        <li v-for="(c, index) in cart" :key="index" class="flower-card">
          <div class="flower-info">
            <span>{{ c.flower.name }}</span>
            <span>₱{{ c.flower.price | formatPrice }} / Qty: {{ c.quantity }}</span>
          </div>
          <div class="flower-actions">
            <button @click="remove(index)" :disabled="!isLoggedIn">Remove</button>
            <button @click="decrement(index)" :disabled="!isLoggedIn">-</button>
            <button @click="increment(index)" :disabled="!isLoggedIn">+</button>
          </div>
        </li>
      </ul>
      <p class="total">Total: ₱{{ calculateTotal() | formatPrice }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const isLoggedIn = ref(false) // Initialize login status

const login = () => {
  // Simulated authentication logic
  if (username.value === 'test' && password.value === '123') {
    // Redirect or perform login actions
    console.log('Login successful!')
    errorMessage.value = '' // Clear error message if any
    isLoggedIn.value = true // Update login status to true when logged in
    window.alert('Login successful!') // Alert for successful login
  } else {
    errorMessage.value = 'Invalid credentials. Please try again.' // Display error message
  }
}

const username = ref('')
const password = ref('')
const errorMessage = ref('')

const buy = (flower) => {
  // Perform buy action
}

const remove = (index) => {
  // Perform remove action
}

const decrement = (index) => {
  // Perform decrement action
}

const increment = (index) => {
  // Perform increment action
}

const calculateTotal = () => {
  // Calculate total
}

const flowers = [
  { id: 1, name: 'Red Rose', price: 50 },
  { id: 2, name: 'Tulip', price: 60 },
  { id: 3, name: 'White Lily', price: 70 },
  { id: 4, name: 'Sunflower', price: 40 },
  { id: 5, name: 'Daisy', price: 45 },
  { id: 6, name: 'Purple Orchid', price: 80 }
]

const formatPrice = (value) => {
  // Format price
}
</script>

<style scoped>
.app-container {
  max-width: 1200px;
  margin: 180px auto; /* Center the container horizontally */
  padding: 10px;
  background-color: #e6e6e6;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: row;
}

.product-container,
.cart-container {
  flex: 1;
  margin-right: 20px;
  overflow-y: auto;
  max-height: 500px;
}

.flower-card {
  margin-bottom: 15px;
  padding: 15px;
  background-color: #3d3636;
}

.flower-info {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.flower-actions {
  margin-top: 10px;
  text-align: right;
}

.flower-actions button {
  background-color: #000;
  color: #fff;
  border: none;
  padding: 8px 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.flower-actions button:disabled {
  background-color: #ccc; /* Disable button color */
  cursor: not-allowed; /* Show disabled cursor */
}

ul {
  list-style-type: none;
}

.total {
  margin-top: 15px;
  text-align: left;
  color: #000;
}

h2 {
  color: #000;
  font-weight: bold;
  margin: 20px 0;
}
</style>
