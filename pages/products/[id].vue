<template>
  <div>
    <Head>
      <Title>Nuxt Learn | {{ product.title }}</Title>
      <Meta name="description" :content="product.description" />
    </Head>
    <ProductDetail :product="product" />
  </div>
</template>

<script setup>
const { id } = useRoute().params;

const { data: product } = await useFetch(
  `https://fakestoreapi.com/products/${id}`
);

if (!product.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "Product not found",
    fatal: true,
  });
}

definePageMeta({
  layout: "products",
});
</script>

<style></style>
