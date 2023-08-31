<script setup lang="ts">
import { Content } from "@prismicio/client";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.FullwidthSlice>([
    "slice",
    "index",
    "slices",
    "context",
  ])
);
</script>

<template>
 <div class="transition-all opacity-0 fadelement">
  <div class="flex gap-5 pb-5">
   <div class="w-full"> <PrismicImage :field="slice.primary.image"/> </div>
    </div>
  </div>
</template>
