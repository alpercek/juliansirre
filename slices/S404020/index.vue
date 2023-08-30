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
  <div class="flex gap-5 pb-5 pl-4 pr-5">
   <div class="w-2/5"> <PrismicImage :field="slice.primary.image401"/> </div>
   <div class="w-2/5"> <PrismicImage :field="slice.primary.image402"/> </div>
   <div class="w-1/5"> <PrismicImage :field="slice.primary.image20"/> </div>
    </div>
</template>
