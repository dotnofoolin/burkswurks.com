<template>
  <div class="columns is-multiline is-mobile has-text-centered">
    <div class="column is-3-tablet is-6-mobile" v-for="edge in $page.products.edges" :key="edge.node.id">
      <g-link :to="`/products/${edge.node.id}`">
        <g-image :src="edge.node.image" />
        <p class="is-size-4">{{ edge.node.name }}</p>
        <p class="is-size-6">{{ edge.node.price | formatMoney }}</p>
      </g-link>
    </div>
  </div>
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
        }
      }
    }
  }
</page-query>

<style>
  img{
    max-width:250px;
    height:150px;
  }
</style>