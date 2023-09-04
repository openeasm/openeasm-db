<script lang="ts" setup>
// import { TwicImg } from '@twicpics/components/vue3'

const props = defineProps<{
  ip: string
  port: string
  country: string
  asn: string
  city: string
  banner: string
  org: string
  service: string
  insert_time: string
}>()

var {ip, port, country, service, asn, org, insert_time,city} = toRefs(props)
if (service !=undefined && service.value!=undefined && service.value.length > 0) {
  service.value = service.value.toLowerCase()
}
console.log(service.value)
// const formattedPrice = computed(() => Number.isNaN(price) ? '-' : price)

// const optimizedImageUrl = computed(() => imageUrl.value.replace('https://images-na.ssl-images-amazon.com/images/', '/product-images/'))
import {ref} from 'vue';

const isCollapsed = ref(true);

function toggleCollapse() {
  isCollapsed.value = !isCollapsed.value;
}
</script>

<template>
  <BaseCard class="product-card">
    <div class="px-5 pb-5">
      <BaseTitle v-if="!service" class="mb-1 text-hot-pink-500 -900 title-xl"
                 style="margin-top: 8px;font-size: larger !important;">
        {{ service }}://{{ ip }}:{{ port }}
      </BaseTitle>
      <BaseTitle v-if="service" class="mb-1 text-hot-pink-500 -900 title-xl"
                 style="margin-top: 8px;font-size: larger !important;">
        {{ service.toLowerCase() }}://{{ ip }}:{{ port }}
      </BaseTitle>
      <div class="flex">
        <div class="w-4/12 bg-gray-200" style="margin-bottom: auto;margin-top: auto;margin-right: 20px">
          <!-- Content for the left div -->
          <div class="flex flex-col mr-1.5 pr-3">
            <div class="flex justify-between pl-3 pt-1">
              <div class="w-1/4 pr-2">
                Service:
              </div>
              <div class="w-3/4 pl-2">
                {{ service }}
              </div>
            </div>
            <div class="flex justify-between pl-3 pt-1">
              <div class="w-1/4 pr-2">
                Location:
              </div>
              <div class="w-3/4 pl-2">
                {{ country }} / {{ city }}
              </div>
            </div>
            <div class="flex justify-between bg-gray-200 pl-3 pt-1">
              <div class="w-1/4 pr-2">
                ASN:
              </div>
              <div class="w-3/4 pl-2">
                {{ asn }}
              </div>
            </div>
            <div class="flex justify-between bg-gray-200 pl-3 pt-1">
              <div class="w-1/4 pr-2">
                ORG:
              </div>
              <div class="w-3/4 pl-2">
                {{ org }}
              </div>
            </div>

            <div class="flex justify-between bg-gray-200 pl-3 pt-1">
              <div class="w-1/4 pr-2">
                TIME:
              </div>
              <div class="w-3/4 pl-2">
                {{ insert_time }}
              </div>
            </div>
          </div>

        </div>
        <div class="w-8/12 bg-gray-300 ">
          <div class="relative mt-">
            <button
                class="absolute top-0 right-0 mt-2 mr-2 p-1 text-gray-600 hover:text-gray-800 focus:outline-none"
                @click="toggleCollapse"
            >
              <!-- Add your collapse icon here, e.g., an arrow -->
              {{ isCollapsed ? '▲' : '▼' }}
            </button>
            <div
                ref="dataContainer"
                :style="{ height: isCollapsed ? '200px' : '100%' }"
                class="overflow-y-auto p-4"
            >
              <!-- Content for the raw data (use the pre tag if needed) -->
              <code style="overflow-x: hidden;overflow-y: hidden;padding-left: 0;white-space: pre-line">
                {{ banner }}
              </code>
            </div>
          </div>
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
