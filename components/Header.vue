<template>
  <Bounded as="header" y-padding="sm">
    <Nav  :alternate-languages="alternateLanguages"
      :navigation="navigation"
      :settings="settings" />
  </Bounded>
</template>

<script>
import Nav from "./Header/Nav.vue";
export default {
  props: {
    navigation: {
      type: Object,
      required: true,
    },
    settings: {
      type: Object,
      required: true,
    },
    alternateLanguages: {
      type: Array,
      default: () => [],
    },
  },
  components: { Nav },
};
</script>
