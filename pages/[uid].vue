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
    <button id="topitop" class="text-[2rem] fixed duration-1000 bottom-28 md:bottom-1/3 right-0 md:right-7 transition-all opacity-0 z-50" @click="toTop()">∴</button>
   <carousel v-if="page?.data.slider.length > 1" :wrapAround="true" :autoplay="5000" :itemsToShow="1.5" :snapAlign="'start'" class="w-screen">
    <slide v-for="(item, i) in page?.data.slider" :key="`page?.data.slider-${i}`" class="">
      <div><PrismicImage :field="item.image" class="object-contain"/>
        <div class="font-metrik text-[0.625rem] pt-1.5 pr-6 justify-end"><PrismicRichText :field="item.fig"/></div> 
        </div>
      
    </slide>

    <template #addons>
      <navigation class=""/>
      <Pagination class=""/>
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
  methods: {
   toTop() {
    window.scrollTo({
  top: 0,
  left: 0,
  behavior: "smooth",
});
  }
  },
}
</script>
<style>
.carousel__pagination{
justify-content: flex-start;
counter-reset: section;
}
:root{
  --vc-pgn-background-color: rgba(255, 0, 0, 0);
  --vc-pgn-active-color: rgba(255, 255, 0, 0);
  --vc-pgn-height: 1rem;
  --vc-pgn-margin: 2px;
}

.carousel__pagination-button::after {
  counter-increment: section;
content: counter(section);
width: 1rem;
  height: 1rem;
  border-radius: 50%;
  border: solid;
  border-width: 1px;
  justify-content: center;
  align-items: center;
  display: flex;
  font-family: METRIK;
  font-size: 14px;

}
</style>