<script lang="ts">
import { components } from "~/slices";
import MasonryWall from '@yeger/vue-masonry-wall'
import { defineComponent } from 'vue'


export default defineComponent({
    
  components: {
    MasonryWall,
  },
  data() {
   
    const items : string[] = [];
    const prismic = usePrismic();
const { data: page } = useAsyncData("[home]", () =>
  prismic.client.getSingle("home")
);

    return {
  
      page,
      components,
      items
    }
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

  mounted() {
    
  var titles = document.getElementsByTagName("section")
  for( var i=0; i<titles.length; i++ ) {this.items.push( titles[i].innerHTML );}
  if (window.innerWidth < 1024) {this.items = [...this.items, '']}
  if (window.innerWidth >= 1024) {
    this.items = [document.getElementById("searchbox")!.innerHTML, ...this.items]
  }
    if (this.items.length < 3) {
      location.reload()
    }
  
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


let bottomimage = document.getElementById("bottomimage")!.children

for (let index = 0; index < bottomimage.length; index++) {
  bottomimage[index].style.opacity = 1
  
}


},
})
</script>

<template>
  <button id="topitop" class="text-[2rem] fixed duration-1000 bottom-28 md:bottom-1/3 right-0 md:right-7 transition-all opacity-0" @click="toTop()">∴</button>
  <div id="enlarge" class="hidden"><div class="fixed inset-0 bg-white opacity-60" onclick="this.parentElement.style.display = 'none'" ></div><img src="" class="opacity-100 w-[500px] fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2"> </div>
  <div id="enlargevideo" class="hidden"><div class="fixed inset-0 bg-white opacity-60" onclick="this.parentElement.style.display = 'none'; this.nextElementSibling.pause()" ></div><video controls src=""  class="opacity-100 w-[500px] fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2"></video> </div>
  <div id="bottomimage" class="fixed bottom-5 left-1/2 -translate-x-1/2 flex h-[30px]"><PrismicImage :field="page.data.bottom_image" class="object-none object-left w-[30px] transition-all opacity-0"/><PrismicImage :field="page.data.bottom_image" class="object-none object-[68%] w-[30px] delay-300 transition-all opacity-0"/><PrismicImage :field="page.data.bottom_image" class="object-none object-right w-[14px] delay-700 transition-all opacity-0"/></div>
<SliceZone
  v-show="false"
    wrapper="main"
    :slices="page?.data.slices ?? []"
    :components="components"
  />
  <div id="searchbox" v-show="false" ><div class="px-1.5"><input class="px-1.5 font-metrik text-xs tracking-tight border border-black rounded-full myInput" onkeyup="
 
 var inpu, filter, ul, li, a, i, txtValue, date, title;
 inpu = document.getElementsByClassName('myInput')[1];
 if (inpu != null) {
   filter = inpu.value.toUpperCase();
 }
 li = document.getElementsByClassName('masonry-item');

 
 for (i = 1; i < li.length; i++) {
   a = li[i].getElementsByTagName('p')[2];
   date = li[i].getElementsByTagName('p')[0];
   title = li[i].getElementsByTagName('p')[1];
   txtValue = a.textContent || a.innerText;
   txtValue += date.textContent || date.innerText;
   txtValue += title.textContent || title.innerText;
   if (txtValue.toUpperCase().indexOf(filter) > -1) {
     li[i].style.maxHeight = '99rem';
   } else {
     li[i].style.maxHeight = '0rem';
   }
 }
 
" type="text" placeholder="Search.."></div></div>
  <div class="px-2.5 pb-[100px]">
  <MasonryWall :items="items" :ssr-columns="1"  :column-width="250" :gap="14">
    <template #default="{ item, index }">
      <div
      v-html="item"
        :style="{ }"
        class=""
      >
      </div>
    </template>
  </MasonryWall>
</div>

</template>
<style>
section{
  width: 19vw
}
.masonry-item{
  transition: all 0.5s;
  overflow: hidden;
}
</style>