<script setup lang="ts">
import { components } from "~/slices";

const prismic = usePrismic();
const { data: page } = useAsyncData("[selected_project]", () =>
  prismic.client.getSingle("selected_project")
);

useHead({
  title: 'Julian Sirre | Selected Projects',
  meta: [
    {
      name: "description",
      content: page.value?.data.meta_description,
    },
  ],
});
</script>

<template>
  <div>
  <SliceZone
    wrapper="main"
    :slices="page?.data.slices ?? []"
    :components="components"
  /></div>
</template>
