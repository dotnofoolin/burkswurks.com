<template>
  <Layout>
    <div>
      <g-image :src="this.$page.product.image" />
      <h1>{{this.$page.product.name}}</h1>
      <p>{{this.$page.product.description}}</p>
      <p>{{this.$page.product.price | formatMoney}}</p>

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
  </Layout>
</template>

<script>
export default {}
</script>

<style>
  img{
    max-width:250px;
    height:150px;
  }
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