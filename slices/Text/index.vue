<script setup lang="ts">
import { Content } from '@prismicio/client'

// The array passed to \`getSliceComponentProps\` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(getSliceComponentProps<Content.TextSlice>(
  ['slice', 'index', 'slices', 'context']
));
</script>

<template>
  <Bounded
    as="section"
    class="bg-white leading-relaxed"
  >
  
  <div class="px-1.5 tracking-tight text-base font-metrik leading-5">
    <PrismicRichText :field="slice.primary.date"/>
    <PrismicRichText class="underline font-bold uppercase pb-6" :field="slice.primary.title"/>
    <PrismicRichText :field="slice.primary.text" class="hyphens-auto"/>
  </div>
  </Bounded>
</template>