<template>
  <div class="container">
    <div class="columns mt-3">
      <div class="column is-two-thirds">
        <nav class="breadcrumb" aria-label="breadcrumbs">
          <ul>
            <li><g-link class="is-italic has-text-weight-bold" to="/">{{ $static.metadata.siteName }}</g-link></li>
            <li><g-link to="/products">Products</g-link></li>
            <li><g-link to="/contact">Contact</g-link></li>
          </ul>
        </nav>
      </div>
      <div class="column">
        <g-link class="snipcart-checkout is-pulled-right">
          <b-button class="is-primary">
            <b-icon pack="fas" icon="shopping-cart" size="is-small"></b-icon>
            <span class="ml-1 snipcart-total-price">{{this.totalPrice | formatMoney }}</span>
          </b-button>
        </g-link>
      </div>
    </div>
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
