<template>
  <div>
    <nav class="wrapper py-6">
      <div class="/px-10 flex justify-between items-center">
          <div class="logo">
            <nuxt-link to="/">
                <h1 class="text-2xl font-semibold text-gray-700"> <span class="text-primary font-bold">james</span>dube</h1>
            </nuxt-link>
          </div>
      
          <div class="navbar hidden md:block">
            <nuxt-link class="nav-link hover:text-primary" to="portfolio">Portfolio</nuxt-link>
            <nuxt-link class="nav-link hover:text-primary" to="blog">Blog</nuxt-link>
            <nuxt-link class="nav-link hover:text-primary" to="about">About</nuxt-link>
            <nuxt-link class="nav-link hover:text-primary" to="contact">Contact</nuxt-link>
            <nuxt-link class="nav-link hover:text-primary" to="credits">Credits</nuxt-link>
          </div>

          <div class="ml-3 flex md:hidden">
            <!-- Mobile menu button -->
            <button @click="toggle" class="flex-center rounded-md">
              <svg :class="[isOpen ? 'hidden' : 'block', 'h-6 w-6']" stroke="currentColor" fill="none" viewBox="0 0 24 24"
                width="24" height="24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
              </svg>
              <svg :class="[isOpen ? 'block' : 'hidden', 'h-6 w-6']" stroke="currentColor" fill="none" viewBox="0 0 24 24"
                width="24" height="24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
              </svg>
            </button>
          </div>
      </div>
    </nav>
    <div :class="[isOpen ? '' : 'hidden', 'md:hidden']">
        <div class="px-2 pt-2 pb-3 sm:px-3 bg-primary">
            <nuxt-link to="portfolio" class="mobile-link focus:outline-none hover:text-gray-500">Projects
            </nuxt-link>
            <nuxt-link to="blog" class="mt-1 mobile-link focus:outline-none hover:text-gray-500">Blog
            </nuxt-link>
            <nuxt-link to="about" class="mt-1 mobile-link focus:outline-none hover:text-gray-500">About
            </nuxt-link>
            <nuxt-link to="contact" class="mt-1 mobile-link focus:outline-none hover:text-gray-500">
              Contact</nuxt-link>
            <nuxt-link to="credits" class="mt-1 mobile-link focus:outline-none hover:text-gray-500">
              Credits</nuxt-link>
        </div>
    </div>
  </div>
</template>


<script>

  export default {
    components:{
      
    },

    data() {
      return {
        isOpen: false
      }
    },

    methods: {
      toggle() {
        this.isOpen = !this.isOpen
      }
    }
  };
</script>

<style>
    .mobile-link{
      @apply block px-3 py-2 text-lg text-gray-900 rounded-md text-white font-medium text-center;
    }

    .nav-link{
      @apply ml-12 font-medium text-lg text-gray-700;
    }
</style>