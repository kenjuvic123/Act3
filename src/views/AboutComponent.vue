<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Flower Shop</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
  </head>
  <body>
    <!-- Main App Container -->
    <div class="app-container">
      <!-- Product List Container -->
      <div class="product-container">
        <h2>Available Flowers</h2>
        <ul>
          <li v-for="f in flowers" :key="f.id" class="flower-card">
            <div class="flower-info">
              <span>{{ f.name }}</span>
              <span>₱{{ f.price | formatPrice }}</span>
            </div>
            <div class="flower-actions">
              <button @click="buy(f)">Buy Now</button>
            </div>
          </li>
        </ul>
      </div>

      <!-- Shopping Cart Container -->
      <div class="cart-container">
        <h2>Your Cart</h2>
        <ul>
          <li v-for="(c, index) in cart" :key="index" class="flower-card">
            <div class="flower-info">
              <span>{{ c.flower.name }}</span>
              <span>₱{{ c.flower.price | formatPrice }} / Qty: {{ c.quantity }}</span>
            </div>
            <div class="flower-actions">
              <button @click="remove(index)">Remove</button>
              <button @click="decrement(index)">-</button>
              <button @click="increment(index)">+</button>
            </div>
          </li>
        </ul>
        <p class="total">Total: ₱{{ calculateTotal() | formatPrice }}</p>
      </div>
    </div>

    <!-- Vue.js Script -->
    <script>
      new Vue({
        el: '.app-container',
        data: {
          flowers: [
            { id: 1, name: 'Red Rose', price: 50 },
            { id: 2, name: 'Tulip', price: 60 },
            { id: 3, name: 'White Lily', price: 70 },
            { id: 4, name: 'Sunflower', price: 40 },
            { id: 5, name: 'Daisy', price: 45 },
            { id: 6, name: 'Purple Orchid', price: 80 }
          ],
          cart: []
        },
        methods: {
          buy(flower) {
            let existing = this.cart.find((item) => item.flower.id === flower.id)
            if (existing) {
              existing.quantity++
            } else {
              this.cart.push({ flower: flower, quantity: 1 })
            }
          },
          remove(index) {
            this.cart.splice(index, 1)
          },
          increment(index) {
            this.cart[index].quantity++
          },
          decrement(index) {
            if (this.cart[index].quantity > 1) {
              this.cart[index].quantity--
            } else {
              this.remove(index)
            }
          },
          calculateTotal() {
            return this.cart.reduce((total, item) => total + item.flower.price * item.quantity, 0)
          }
        },
        filters: {
          formatPrice(value) {
            return value.toLocaleString('en-US', { minimumFractionDigits: 2 })
          }
        }
      })
    </script>

    <style>
      /* New styling to differentiate from the original */
      .app-container {
        max-width: 800px;
        margin: 20px auto;
        padding: 20px;
        background-color: #f0f0f0;
        border-radius: 10px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        display: flex;
        flex-direction: row;
      }

      .product-container,
      .cart-container {
        flex: 1;
        margin-right: 20px;
        overflow-y: auto;
        max-height: 400px;
      }

      .flower-card {
        margin-bottom: 15px;
        padding: 15px;
        border: 1px solid #000;
        background-color: #fff;
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

      ul {
        list-style-type: none;
      }

      .total {
        margin-top: 15px;
        text-align: left;
        color: #000;
      }
    </style>
  </body>
</html>
