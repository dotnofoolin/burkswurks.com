<template>
  <Layout>
    <Products />
  </Layout>
</template>

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
          variant
        }
      }
    }
  }
</page-query>

<script>
  import Products from "@/components/Products"
  
  export default {
    metaInfo: {
      title: 'Products'
    },
    components: {
      Products
    }
  }
</script>