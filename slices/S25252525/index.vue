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
   <div class="transition-all opacity-0 fadelement">
  <div class="flex gap-5 pb-5 pl-4 pr-5">
   <div class="w-1/4"> <PrismicImage :field="slice.primary.image1"/> </div>
   <div class="w-1/4"> <PrismicImage :field="slice.primary.image2"/> </div>
   <div class="w-1/4"> <PrismicImage :field="slice.primary.image3"/> </div>
   <div class="w-1/4"> <PrismicImage :field="slice.primary.image4"/> </div>
    </div>
  </div>
</template>
