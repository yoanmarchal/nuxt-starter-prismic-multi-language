<template>
  <nav class="relative flex flex-wrap items-center justify-between mb-3">
    <div
      class="container px-4 mx-auto flex flex-wrap items-center justify-between"
    >
      <div
        class="
          w-full
          relative
          flex
          justify-between
          items-center
          lg:w-auto lg:static lg:block lg:justify-start
        "
      >
        <Logo :settings="settings" />
        <button
          class="
            cursor-pointer
            text-xl
            leading-none
            px-3
            py-1
            border border-solid border-transparent
            rounded
            bg-transparent
            block
            lg:hidden
            outline-none
            focus:outline-none
          "
          type="button"
          @click="toggleNav()"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="w-5 h-5"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M4 6h16M4 12h16M4 18h16"
            />
          </svg>
        </button>
      </div>
      <div
        :class="{ hidden: !showMenu, flex: showMenu }"
        class="lg:flex lg:flex-grow items-center"
      >
        <ul class="flex flex-col lg:flex-row list-none ml-auto">
          <li
            v-for="item in navigation.data.links"
            :key="$prismic.asText(item.label)"
            class="
              px-3
              py-2
              flex
              items-center
              text-xs
              uppercase
              font-bold
              leading-snug
              hover:opacity-75
            "
          >
            <PrismicLink :field="item.link">
              {{ $prismic.asText(item.label) }}
            </PrismicLink>
          </li>
          <li
            v-for="lang in alternateLanguages"
            :key="lang.lang"
            class="
              px-3
              py-2
              flex
              items-center
              text-xs
              uppercase
              font-bold
              leading-snug
              hover:opacity-75
            "
          >
            <PrismicLink :field="{ ...lang, link_type: 'Document' }">
              <span class="sr-only">{{ lang.lang }}</span>
              <span
                class="fi"
                :class="`fi-${lang.lang.substring(3).toLowerCase()}`"
              />
            </PrismicLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
import Logo from "./Logo.vue";
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
  data() {
    return {
      showMenu: false,
    };
  },
  methods: {
    toggleNav() {
      this.showMenu = !this.showMenu;
    },
  },
  components: { Logo },
};
</script>

<style>
</style>