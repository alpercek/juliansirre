<script setup lang="ts">
import { components } from '~/slices'
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'

const prismic = usePrismic()
const route = useRoute()
const { data: page } = useAsyncData('[uid]', () =>
  prismic.client.getByUID('page', route.params.uid as string || 'home')
)
const settings = useSettings()

useHead({
  title: computed(() => `${prismic.asText(page.value?.data.title)} | ${prismic.asText(settings.value?.data.siteTitle)}`)
})
</script>


<template>
  <div>
   <carousel v-if="page?.data.slider.length > 1" :wrapAround="true" :autoplay="5000"  class="w-screen">
    <slide v-for="(item, i) in page?.data.slider" :key="`page?.data.slider-${i}`">
      <div><PrismicImage :field="item.image" class="w-screen"/>
        <div class="group-hover:opacity-100 opacity-0 transition-all flex font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="item.fig"/></div> 
        </div>
      
    </slide>

    <template #addons>
      <navigation class="group-hover:opacity-100 opacity-0 transition-all !hidden md:!flex"/>
    </template>
  </carousel>
  <SliceZone
    wrapper="main"
    :slices="page?.data.slices ?? []"
    :components="components"
  />
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