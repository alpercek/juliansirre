<script setup lang="ts">
import { Content } from "@prismicio/client";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.S25252525Slice>([
    "slice",
    "index",
    "slices",
    "context",
  ])
);
</script>

<template>
   <div class="transition-all opacity-0 duration-500 delay-300 fadelement">
  <div class="flex gap-5 pb-5 pl-4 pr-5">
   <div class="w-1/4 group/item"> <PrismicImage :field="slice.primary.image1" class="w-screen"/> 
    <div class="group-hover/item:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="slice.primary.title1"/>&nbsp;<PrismicRichText :field="slice.primary.year1"/>&nbsp;<PrismicRichText :field="slice.primary.fig1"/></div> 
  </div>
   <div class="w-1/4 group/item1"> <PrismicImage :field="slice.primary.image2" class="w-screen"/> 
    <div class="group-hover/item1:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="slice.primary.title2"/>&nbsp;<PrismicRichText :field="slice.primary.year2"/>&nbsp;<PrismicRichText :field="slice.primary.fig2"/></div> 
  </div>
   <div class="w-1/4 group/item2"> <PrismicImage :field="slice.primary.image3" class="w-screen"/> 
    <div class="group-hover/item2:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="slice.primary.title3"/>&nbsp;<PrismicRichText :field="slice.primary.year3"/>&nbsp;<PrismicRichText :field="slice.primary.fig3"/></div> 
  </div>
   <div class="w-1/4 group/item3"> <PrismicImage :field="slice.primary.image4" class="w-screen"/> 
    <div class="group-hover/item3:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="slice.primary.title4"/>&nbsp;<PrismicRichText :field="slice.primary.year4"/>&nbsp;<PrismicRichText :field="slice.primary.fig4"/></div> 
  </div>
    </div>
  </div>
</template>
