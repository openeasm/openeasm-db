<script lang="ts" setup>
import { AisInfiniteHits } from 'vue-instantsearch/vue3/es'
</script>

<template>
  <AisInfiniteHits>
    <template
      #default="{
        items,
        refineNext,
        isLastPage,
      }"
    >
      <div class="items mb-1">
        <ProductCard
          v-for="product in items"
          :key="product.id"
          :ip="product.ip"
          :port="product.port"
          :country="product.country"
          :banner="product.banner"
          :asn="product.asn"
          :city="product.city"
          :org="product.org"
          :insert_time="product.insert_time"
          :service = "product.service"
        />
      </div>
      <div v-if="!isLastPage">
        <BaseButton size="large" color="dodger-blue" class="m-auto" @click="refineNext">
          Show more results
        </BaseButton>
      </div>
    </template>
  </AisInfiniteHits>
</template>

<style src="~/assets/css/components/results-grid.css" scoped />
