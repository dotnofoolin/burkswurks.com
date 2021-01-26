<template>
  <Layout>
    <div class="block">
      <p>Howdy! Welcome, and thanks for your support.</p>
    </div>
    <hr/>
    <Products />
  </Layout>
</template>

<script>
import Products from "@/components/Products.vue"

export default {
  metaInfo: {
    title: 'Home'
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
