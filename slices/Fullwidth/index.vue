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
  <div :class="{' pr-5 pl-4': slice.variation === 'paddingOnTheSides'}" class="flex pb-5 gap-5 group fadelement duration-500 delay-300 transition-all opacity-0">
  <carousel v-if="slice.items.length > 1" :wrapAround="true" :autoplay="5000"  class="w-screen">
    <slide v-for="(item, i) in slice.items" :key="`slice-item-${i}`">
      <div> <PrismicLink :field="slice.primary.link"><PrismicImage :field="item.image" class="w-screen"/> </PrismicLink>
        <div class="group-hover:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="item.title"/>&nbsp;<PrismicRichText :field="item.year"/>&nbsp;<PrismicRichText :field="item.fig"/></div> 
        </div>
      
    </slide>

    <template #addons>
      <navigation class="group-hover:opacity-100 opacity-0 transition-all !hidden md:!flex"/>
    </template>
  </carousel>
  <div v-else><PrismicImage :field="slice.items[0].image" class="w-screen"/>
   <div class="group-hover:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="slice.items[0].title"/>&nbsp;<PrismicRichText :field="slice.items[0].year"/>&nbsp;<PrismicRichText :field="slice.items[0].fig"/></div> 
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