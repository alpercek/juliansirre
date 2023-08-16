<script setup lang="ts">
import { Content } from '@prismicio/client'

// The array passed to \`getSliceComponentProps\` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(getSliceComponentProps<Content.TextWithImageSlice>(
  ['slice', 'index', 'slices', 'context']
));
</script>

<template>
  <Bounded
    as="section"
    class="bg-white"
  >
    <div :class="{ 'flex-col-reverse': slice.variation === 'textOnTop'}" class="gap-3.5 flex flex-col">
      <div class="px-1.5 tracking-tight text-sm font-metrik leading-5">
    <PrismicRichText :field="slice.primary.date"/>
    <PrismicRichText class="underline uppercase pb-6" :field="slice.primary.title"/>
    <PrismicRichText :field="slice.primary.text"/>
  </div>
      
        <div v-if="slice.items.length > 0" class="px-1.5 flex gap-1.5 flex-col">
      <div v-for="(item, i) in slice.items" :key="`slice-item-${i}`">
        <PrismicImage :field="item.image" onclick="
          if(window.innerWidth > 640){
        let enlarge = document.getElementById('enlarge')
        let emage = enlarge.getElementsByTagName('img')[0]
        emage.src = this.src
        enlarge.style.display = 'block'
          }
        " class="bg-gray-100"/>
        <div v-if="item.video.url" class="pt-1.5"><video onclick="
          if(window.innerWidth > 640){
        let enlarge = document.getElementById('enlargevideo')
        let emage = enlarge.getElementsByTagName('video')[0]
        emage.src = this.src
        enlarge.style.display = 'block'
          }
          else {this.play()}
        " type="video/mp4" playsinline controls :src="item.video.url"></video></div>
      </div>
    </div>
    <div v-if="slice.variation === 'imageBetween'" class="px-1.5 tracking-tight text-sm font-metrik leading-5"><PrismicRichText :field="slice.primary.text"/></div>
    </div>
  </Bounded>
</template>
