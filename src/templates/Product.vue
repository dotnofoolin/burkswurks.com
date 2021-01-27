<template>
  <Layout>
    <div class="columns is-mobile is-centered">
      <div class="column is-half-tablet">
        <div class="card">
          <div class="card-image ml-3 mt-3">
            <figure class="image">
              <g-image :src="this.$page.product.image" />
            </figure>
          </div>
          <div class="card-content">
            <div class="media">
              <div class="media-content">
                <p class="title is-4">{{this.$page.product.name}}</p>
                <p class="subtitle is-6">{{this.$page.product.price | formatMoney}}</p>
              </div>
            </div>

            <div class="content">
              <p>{{this.$page.product.description}}</p>

              <b-button v-if="this.$page.product.variant == 'sizes'"
                class="is-primary snipcart-add-item"
                :data-item-id="this.$page.product.id"
                :data-item-description="this.$page.product.description"
                :data-item-image="this.$page.product.image"
                :data-item-price="this.$page.product.price"
                :data-item-name="this.$page.product.name"
                :data-item-url="`/products/${this.$page.product.id}`"
                data-item-custom1-name="Size"
                data-item-custom1-options="S|M|L|XL|2XL|3XL"
                data-item-custom1-required="true"
              >
                Add To Cart
              </b-button>

              <b-button v-if="this.$page.product.variant != 'sizes'"
                class="is-primary snipcart-add-item"
                :data-item-id="this.$page.product.id"
                :data-item-description="this.$page.product.description"
                :data-item-image="this.$page.product.image"
                :data-item-price="this.$page.product.price"
                :data-item-name="this.$page.product.name"
                :data-item-url="`/products/${this.$page.product.id}`"
              >
                Add To Cart
              </b-button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </Layout>
</template>

<script>
export default {}
</script>

<style>
</style>

<page-query>
  query ($id: ID!) {
    product(id: $id) {
      id
      name
      image
      description
      price
      variant
    }
  }
</page-query>