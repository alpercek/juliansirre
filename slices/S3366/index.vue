<script setup lang="ts">
import { Content } from "@prismicio/client";
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.S3366Slice>([
    "slice",
    "index",
    "slices",
    "context",
  ])
);
</script>

<template>
  <div :class="{'flex-row-reverse': slice.variation === 'swappedL66R33'}" class="flex gap-5 fadelement transition-all opacity-0">
    <div class="w-1/3">
  <PrismicImage :field="slice.primary.l33"/>
    </div>
  <carousel v-if="slice.items.length > 1" :wrapAround="true" class="w-2/3 group">
    <slide v-for="(item, i) in slice.items" :key="`slice-item-${i}`">
      <PrismicImage :field="item.r66" />
    </slide>

    <template #addons>
      <navigation class="group-hover:opacity-100 opacity-0 transition-all"/>
    </template>
  </carousel>
  <div v-else class="w-2/3"><PrismicImage :field="slice.items[0].r66"/></div>
  </div>
</template>
<script lang="ts">
export default {
  name: 'App',
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },
}
</script>
<style>
:root{
--vc-clr-primary: #C7C7C7;
--vc-nav-color-hover: #C7C7C7;
}
.carousel__icon{
  display: none;
}
.carousel__next{
  border: solid;
    border-width: 0 3px 3px 0;
    display: inline-block;
    padding: 9px;
    transform: rotate(-45deg);
    -webkit-transform: rotate(-45deg);
}
.carousel__prev{
  border: solid;
    border-width: 0 3px 3px 0;
    display: inline-block;
    padding: 9px;
    transform: rotate(135deg);
    -webkit-transform: rotate(135deg);
}
</style>