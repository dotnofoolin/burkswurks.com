<template>
  <Layout>

    <strong>Yo! Welcome, and thanks for your support.</strong>

    <hr/>

    <Products />

  </Layout>
</template>

<script>
import Products from "@/components/Products.vue"

export default {
  metaInfo: {
    title: 'BurksWurks'
  },
  components: {
    Products
  }
}
</script>

<style>
</style>

<page-query>
  query{
    products: allProduct{
      edges{
        node{
          id
          name
          image
          description
          price
        }
      }
    }
  }
</page-query>
