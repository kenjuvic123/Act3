<template>
  <main>
    <TheWelcome />

    <!-- Login Form -->
    <form @submit.prevent="login" class="login-form">
      <div class="form-group">
        <label for="username">Username:</label>
        <input type="text" id="username" v-model="username" required />
      </div>
      <div class="form-group">
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required />
      </div>
      <button type="submit">Login</button>
      <p v-if="errorMessage" class="error-message">{{ errorMessage }}</p>
    </form>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const username = ref('')
const password = ref('')
const errorMessage = ref('')

const login = () => {
  // Simulated authentication logic
  if (username.value === 'test' && password.value === '123') {
    // Redirect or perform login actions
    console.log('Login successful!')
    errorMessage.value = '' // Clear error message if any
    window.alert('Login successful!') // Alert for successful login
  } else {
    errorMessage.value = 'Invalid credentials. Please try again.' // Display error message
  }
}
</script>

<style scoped>
.main {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.login-form {
  margin-top: 20px;
}

.form-group {
  margin-bottom: 15px;
}

input {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 8px 16px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.error-message {
  color: red;
  margin-top: 10px;
}
</style>
