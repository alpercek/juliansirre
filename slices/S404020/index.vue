<script setup lang="ts">
import { Content } from "@prismicio/client";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.S404020Slice>([
    "slice",
    "index",
    "slices",
    "context",
  ])
);
</script>

<template>
  <div class="transition-all opacity-0 duration-300 fadelement">
  <div class="flex gap-5 pb-5 pl-4 pr-5">
   <div class="w-2/5 group/item"> <PrismicImage :field="slice.primary.image401" class="w-screen"/> 
    <div class="group-hover/item:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="slice.primary.title401"/>&nbsp;<PrismicRichText :field="slice.primary.year401"/>&nbsp;<PrismicRichText :field="slice.primary.fig401"/></div> 
  </div>
   <div :class="{'flex-row-reverse': slice.variation === '402040'}" class="flex gap-5 w-3/5">
   <div class="w-4/6 group/item1"> <PrismicImage :field="slice.primary.image402" class="w-screen"/> 
    <div class="group-hover/item1:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="slice.primary.title402"/>&nbsp;<PrismicRichText :field="slice.primary.year402"/>&nbsp;<PrismicRichText :field="slice.primary.fig402"/></div> 
  </div>
   <div class="w-2/6 group/item2"> <PrismicImage :field="slice.primary.image20" class="w-screen"/>
    <div class="group-hover/item2:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="slice.primary.title20"/>&nbsp;<PrismicRichText :field="slice.primary.year20"/>&nbsp;<PrismicRichText :field="slice.primary.fig20"/></div> 
  </div>
  </div>
    </div>
  </div>
</template>
