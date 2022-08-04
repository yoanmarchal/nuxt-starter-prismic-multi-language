<template>
  <Bounded
    as="section"
    :class="{
      'bg-slate-100': slice.variation === 'lightSlate',
      'bg-white': slice.variation === 'white'
    }"
  >
    <div class="relative">
      <div v-if="slice.primary.withAccent" class="absolute -top-4 -left-4 w-1/3">
        <div class="aspect-w-1 aspect-h-1 bg-slate-200/50" />
      </div>
    </div>
    <nuxt-img
      v-if="slice.primary.image.url"
      :src="slice.primary.image.url"
      class="relative"
    />
  </Bounded>
</template>

<script>
import { getSliceComponentProps } from '@prismicio/vue/components'

export default {
  // The array passed to `getSliceComponentProps` is purely optional.
  // Consider it as a visual hint for you when templating your slice.
  props: getSliceComponentProps(['slice', 'index', 'slices', 'context'])
}
</script>
