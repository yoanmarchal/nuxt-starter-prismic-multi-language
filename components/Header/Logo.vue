<template>
  <a
    class="
      text-sm
      font-bold
      leading-relaxed
      inline-block
      mr-4
      py-2
      whitespace-nowrap
      uppercase
    "
    href="/"
  >
    <span class="sr-only">Home</span>
    <NuxtLink :to="localePath('/')">
      <nuxt-img
      v-if="settings.data.logo.url"
      style="max-width: 150px; max-height: 100px"
      provider="prismic" :src="settings.data.logo.url" />
    </NuxtLink>
  </a>
</template>

<script>
export default {
  props: {
    settings: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style>
</style>
