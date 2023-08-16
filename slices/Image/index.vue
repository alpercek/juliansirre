<script setup lang="ts">
import { Content } from '@prismicio/client'

// The array passed to \`getSliceComponentProps\` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(getSliceComponentProps<Content.ImageSlice>(
  ['slice', 'index', 'slices', 'context']
)
);

</script>

<template>
  <Bounded
    as="section"
    class="bg-white"
    :class="{
      'pt-0 md:pt-0': index === 0
    }"
  ><p class="hidden" >{{ $prismic.asText(slice.primary.tags) }}</p>
  <p class="hidden" ></p>
  <p class="hidden" ></p>
    <div v-if="slice.items.length > 0" class="px-1.5 flex gap-1.5 flex-col">
      <div v-for="(item, i) in slice.items" :key="`slice-item-${i}`">
        <PrismicImage onclick="
          if(window.innerWidth > 640){
        let enlarge = document.getElementById('enlarge')
        let emage = enlarge.getElementsByTagName('img')[0]
        emage.src = this.src
        enlarge.style.display = 'block'
          }
        " :field="item.image" class="bg-gray-100"/>
        <div v-if="item.video.url" class="pt-1.5"><video onclick="
          if(window.innerWidth > 640){
        let enlarge = document.getElementById('enlargevideo')
        let emage = enlarge.getElementsByTagName('video')[0]
        emage.src = this.src
        enlarge.style.display = 'block'
          }
          else {this.play()}
        " type="video/mp4" playsinline :src="item.video.url"></video></div>
      </div>
    </div>
  </Bounded>
</template>
<script lang="ts">


</script>