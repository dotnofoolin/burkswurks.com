<template>
  <div class="container is-fluid">
    <nav class="level mt-4">
      <div class="level-left">
        <div class="level-item">
          <p>
            <g-link class="is-italic has-text-weight-bold" to="/">{{ $static.metadata.siteName }}</g-link>
          </p>
        </div>
        <div class="level-item"><g-link to="/products">Products</g-link></div>
        <div class="level-item"><g-link to="/contact">Contact</g-link></div>
      </div>
      <div class="level-right">
        <p class="level-item">
          <g-link class="snipcart-checkout is-pulled-right">
          <b-button class="is-primary">
            <b-icon pack="fas" icon="shopping-cart" size="is-small"></b-icon>
            <span class="snipcart-total-price">{{this.totalPrice | formatMoney }}</span>
          </b-button>
        </g-link>
        </p>
      </div>
    </nav>
    <slot/>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
  export default {
    data: function() {
        return {
          totalPrice: 0
        }
      },
    methods: {
      getTotalPrice: function() {
        return Snipcart.store.getState().cart.total
      }
    },
    mounted: function() {
      this.totalPrice = this.getTotalPrice()
    }
  }
</script>

<style>
  body {
    font-family: "Montserrat";
  }
</style>
