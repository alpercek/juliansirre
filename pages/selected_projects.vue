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
    class="pb-9"
    wrapper="main"
    :slices="page?.data.slices ?? []"
    :components="components"
  /></div>
</template>
<script lang="ts">
export default {
mounted(){
  let elements = document.getElementsByClassName('fadelement')
  let bottom
  if ( window.innerHeight > window.innerWidth ){  bottom = window.innerHeight }
  else { bottom = window.innerHeight+(window.innerHeight/2)}
  for (let index = 0; index < elements.length; index++) {
  if (elements[index].getBoundingClientRect().bottom < bottom) {
    elements[index].style.opacity = "1"
  }
  else{
    elements[index].style.opacity = "0"
  }
  
 }
 document.addEventListener('scroll', function checkfade(){
 for (let index = 0; index < elements.length; index++) {
  if (elements[index].getBoundingClientRect().bottom < bottom) {
    elements[index].style.opacity = "1"
  }
  else{
    elements[index].style.opacity = "0"
  }
  
 }
})
}
}
</script>