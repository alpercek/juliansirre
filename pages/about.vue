<script setup lang="ts">
import { components } from "~/slices";

const prismic = usePrismic();
const { data: page } = useAsyncData("[about]", () =>
  prismic.client.getSingle("about")
);

useHead({
  title: 'Julian Sirre | About',
  meta: [
    {
      name: "description",
      content: page.value?.data.meta_description,
    },
  ],
});
</script>

<template>
  <div class="mr-40">
    <div class="flex pl-4 gap-5 font-metrik text-sm pb-8">
      <div class="w-1/3">
        <p>Julian Sirre (1983)</p>
        <PrismicRichText :field="page?.data.location"/>
      </div>
      <div class="w-1/3">
     <PrismicRichText :field="page?.data.address"/>
     <PrismicRichText :field="page?.data.address2"/>
      </div>
    </div>
  <SliceZone
    class="columns-3 pl-4 gap-5"
    wrapper="main"
    :slices="page?.data.slices ?? []"
    :components="components"
  />
</div>
</template>
