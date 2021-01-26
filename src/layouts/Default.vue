<template>
  <div class="layout">
    <header class="header">
      <strong>
        <g-link to="/">{{ $static.metadata.siteName }}</g-link>
      </strong>
      <nav class="nav">
        <g-link class="nav__link" to="/contact">Contact</g-link>
        <g-link class="nav__link" to="/products">Products</g-link>
        <g-link class="nav__link snipcart-checkout">
          <b-button class="is-primary is-small">
            <b-icon pack="fas" icon="shopping-cart" size="is-small"></b-icon>
            <span class="ml-1 snipcart-total-price">{{this.totalPrice | formatMoney }}</span>
          </b-button>
        </g-link>
      </nav>
    </header>
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
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
}

.layout {
  max-width: 760px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 80px;
}

.nav__link {
  margin-left: 20px;
}
</style>
