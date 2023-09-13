<script setup lang="ts">
</script>

<template>
    <div class="flex flex-wrap justify-between px-3.5 pt-3.5 pb-6">
      <NuxtLink :key="$route.path" to="/">
      <img src="/favicon.ico">
      </NuxtLink>
      <nav>
        <ul class="flex flex-wrap gap-3.5 mb-1.5 md:text-sm text-[1.313rem]">
          <li class="tracking-tight font-metrik">
            <NuxtLink :key="$route.path" to="selected_projects">
              SELECTED PROJECTS
            </NuxtLink></li><li class="tracking-tight font-metrik">
          <NuxtLink :key="$route.path" to="about">
              ABOUT
          </NuxtLink>
          </li>
        </ul>
      </nav>
    </div>
</template>

