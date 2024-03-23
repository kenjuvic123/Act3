<template>
  <link
    rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/bootstrap@4.4.1/dist/css/bootstrap.min.css"
    integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh"
    crossorigin="anonymous"
  />
  <div class="container-fluid">
    <header>
      <nav class="navbar navbar-expand-lg navbar-light bg-light flex-column">
        <router-link to="/" class="navbar-brand mb-0 h1">Flower Shop</router-link>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <div class="btn-group" role="group" aria-label="Button group with nested dropdown">
            <button
              :class="{ 'btn-secondary': !isLoggedIn, 'btn-success': isLoggedIn }"
              type="button"
            >
              status
            </button>
          </div>
          <ul class="navbar-nav mb-2 mb-lg-0">
            <li class="nav-item">
              <router-link to="/" class="nav-link">Login Form</router-link>
            </li>
            <li class="nav-item">
              <router-link to="/about" class="nav-link">Shopping Cart</router-link>
            </li>
            <li class="nav-item">
              <router-link to="/" class="btn btn-danger">Logout</router-link>
            </li>
          </ul>
        </div>
      </nav>
    </header>
    <RouterView />
  </div>
</template>

<script setup lang="ts">
import { RouterLink } from 'vue-router'
import { ref } from 'vue'

const isLoggedIn = ref(false) // Initialize login status
</script>

<style scoped>
/* Add custom styles here if needed */
</style>
