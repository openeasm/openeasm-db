<script lang="ts" setup>
// import { TwicImg } from '@twicpics/components/vue3'

const props = defineProps<{
  ip: string
  port: string
  country: string
  banner: string
  service: string
}>()

const {ip, port, country, service} = toRefs(props)

// const formattedPrice = computed(() => Number.isNaN(price) ? '-' : price)

// const optimizedImageUrl = computed(() => imageUrl.value.replace('https://images-na.ssl-images-amazon.com/images/', '/product-images/'))
</script>

<template>
  <BaseCard class="product-card">
    <div class="px-5 pb-5">
      <BaseTitle class="mb-1 text-hot-pink-500 -900 title-xl" style="margin-top: 8px;font-size: larger !important;">
        {{ service }}://{{ ip }}:{{ port }}
      </BaseTitle>
      <div class="grid grid-cols-4 gap-4">
        <div>
          <BaseText
              class="mb-2 text-valhalla-900 "
              size="m"
          >
            {{ country }}
          </BaseText>
        </div>
        <div>
          <BaseText
              class="mb-2 text-valhalla-900 "
              size="m"
          >
            {{ country }}
          </BaseText>
        </div>

      </div>
    </div>
  </BaseCard>
</template>

<style scoped>
.product-card {
  max-width: 100%;
  transition: transform ease-in-out 150ms;
}

.product-card:hover {
  box-shadow: 0px 0px 14px 8px rgba(77, 90, 125, 0.1), 0px 4px 66px rgba(77, 90, 125, 0.04);
  transform: translateY(-5px);
}

.product-name {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}

.product-rating {
  display: flex;
  align-items: baseline;
}
</style>
