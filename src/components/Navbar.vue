<template>
  <nav
    class="bg-white border-gray-200 dark:bg-gray-900 fixed w-full top-0 start-0 h-16 px-8 z-10"
  >
    <div
      class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto py-4"
    >
      <button
        @click="backToTop"
        class="flex items-center space-x-3 rtl:space-x-reverse"
      >
        <span
          class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white"
          >EASY SUPPLY.</span
        >
      </button>
      <button
        @click="toggleMobileOpen"
        data-collapse-toggle="navbar-default"
        type="button"
        class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
        aria-controls="navbar-default"
        aria-expanded="false"
      >
        <svg
          class="w-5 h-5"
          aria-hidden="true"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 17 14"
        >
          <path
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M1 1h15M1 7h15M1 13h15"
          />
        </svg>
      </button>
      <div
        :class="[
          isMobileOpen ? 'block' : 'hidden',
          'w-full md:block md:w-auto',
        ]"
        id="navbar-default"
      >
        <ul
          class="font-medium flex flex-col p-4 md:p-0 border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 rtl:space-x-reverse md:mt-0 md:border-0 md:bg-white dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700"
        >
          <li @click="closeMobile" v-for="link in links">
            <a
              :href="link.href"
              class="block py-2 px-3 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:font-bold md:p-0"
              >{{ link.text }}</a
            >
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from "vue";

const links = ref([
  { href: "#services", text: "Services" },
  { href: "#catalogue", text: "Catalogue" },
  { href: "#certifications", text: "Certifications" },
  { href: "#contact", text: "Contact" },
]);

const backToTop = () => {
  // window.scrollTo({ top: 0, left: 0, behavior: "smooth" });
  window.location.href = "#";
};

const isMobileOpen = ref(false);

const toggleMobileOpen = () => {
  isMobileOpen.value = !isMobileOpen.value;
};

const closeMobile = () => {
  isMobileOpen.value = false;
};
</script>

<style>
html {
  scroll-behavior: smooth;
}

#services,
#catalogue,
#certifications,
#contact {
  scroll-margin-top: 4rem;
}
</style>
