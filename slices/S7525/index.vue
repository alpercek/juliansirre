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
  <div :class="{'flex-row-reverse': slice.variation === '75OnTheLeft'}" class="flex pb-5 pl-4 pr-5 gap-5 duration-500 delay-300 fadelement transition-all opacity-0">
    <div class="w-1/4 group/edit">
  <PrismicImage :field="slice.primary.image25" class="w-screen"/>
  <div class="group-hover/edit:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="slice.primary.title25"/>&nbsp;<PrismicRichText :field="slice.primary.year25"/>&nbsp;<PrismicRichText :field="slice.primary.fig25"/></div> 
    </div>
    <div class="group/item w-3/4">
  <carousel v-if="slice.items.length > 1" :wrapAround="true" class="w-full">
    <slide v-for="(item, i) in slice.items" :key="`slice-item-${i}`">
      <div><PrismicImage :field="item.image75" class="w-screen"/>
        <div class="group-hover/item:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="item.title75"/>&nbsp;<PrismicRichText :field="item.year75"/>&nbsp;<PrismicRichText :field="item.fig75"/></div> 
        </div>
    </slide>

    <template #addons>
      <navigation class="group-hover/item:opacity-100 opacity-0 transition-all"/>
    </template>
  </carousel>
  <div v-else class="w-full"><PrismicImage :field="slice.items[0].image75" class="w-screen"/>
    <div class="group-hover/item:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="slice.items[0].title75"/>&nbsp;<PrismicRichText :field="slice.items[0].year75"/>&nbsp;<PrismicRichText :field="slice.items[0].fig75"/></div> 
  </div>
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
    transform: rotate(-45deg) translate(-20px, -20px);
    -webkit-transform: rotate(-45deg) translate(-20px, -20px);
}
.carousel__prev{
  border: solid;
    border-width: 0 3px 3px 0;
    display: inline-block;
    padding: 9px;
    transform: rotate(135deg) translate(-20px, -20px);
    -webkit-transform: rotate(135deg) translate(-20px, -20px);
}
</style>