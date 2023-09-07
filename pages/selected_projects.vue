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
    <button id="topitop" class="text-[2rem] fixed duration-1000 bottom-28 md:bottom-1/3 right-0 md:right-7 transition-all opacity-0 z-50" @click="toTop()">∴</button>
  <SliceZone
    class="pb-9"
    wrapper="main"
    :slices="page?.data.slices ?? []"
    :components="components"
  /></div>
</template>
<script lang="ts">
export default {
  methods: {
   toTop() {
    window.scrollTo({
  top: 0,
  left: 0,
  behavior: "smooth",
});
  }
  },
mounted(){
  let elements = document.getElementsByClassName('fadelement')
  let bottom = window.innerHeight + 20
  for (let index = 0; index < elements.length; index++) {
  if (elements[index].getBoundingClientRect().top < bottom) {
    elements[index].style.opacity = "1"
  }
  else{
    elements[index].style.opacity = "0"
  }
  
 }
 document.addEventListener('scroll', function checkfade(){
 for (let index = 0; index < elements.length; index++) {
  if (elements[index].getBoundingClientRect().top < bottom) {
    elements[index].style.opacity = "1"
  }
  else{
    elements[index].style.opacity = "0"
  }
  
 }
})

var timer = null
    document.addEventListener("scroll", function(){ 
   
   if (timer !== null) {
    document.getElementById("topitop")!.style.opacity = "1"
    clearTimeout(timer)
   } 
   timer = setTimeout(function(){
    document.getElementById("topitop")!.style.opacity = "0"
   },5000)
   
   

}, false);
}
}
</script>
<style>
.fadelement:first-child{
opacity: 1 !important;
}
</style>