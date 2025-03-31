<template>
  <ProductDetails :product="product"></ProductDetails>
</template>

<script setup>
import ProductDetails from "~/components/ProductDetails.vue";
const { id } = useRoute().params;

const uri = "https://fakestoreapi.com/products/" + id;

// fetch the product
const { data: product } = await useFetch(uri, { key: id });

if (!product.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "Product Not Found",
    fatal: true,
  });
}

definePageMeta({
  layout: "products",
});
</script>

<style lang="scss" scoped></style>
