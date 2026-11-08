<script setup lang="ts">
// import { RouterView } from 'vue-router'

import MenuItem from './components/MenuItem.vue'
import { onMounted, onUnmounted, ref } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import heroImage from '@/assets/images/turkey.jpg'
import menuImage from '@/assets/images/thanksgiving dinner table.jpg'

const story = ref<HTMLDivElement | null>(null)
let animations: ReturnType<typeof gsap.matchMedia> | undefined

onMounted(() => {
  const root = story.value
  if (!root) return

  gsap.registerPlugin(ScrollTrigger)
  animations = gsap.matchMedia()

  animations.add(
    '(min-width: 64rem) and (prefers-reduced-motion: no-preference)',
    () => {
      gsap
        .timeline({
          defaults: { ease: 'none', duration: 1 },
          scrollTrigger: {
            trigger: root,
            start: 'top top',
            end: () => `+=${window.innerHeight * 0.5}`,
            scrub: true,
            invalidateOnRefresh: true,
          },
        })
        .fromTo('.visual', { width: '100%' }, { width: '33.333%' }, 0)
        .fromTo('.hero-title', { opacity: 1 }, { opacity: 0 }, 0)
        .fromTo('.side-image', { opacity: 0 }, { opacity: 1 }, 0)
        .fromTo('.menu-items', { autoAlpha: 0, y: 24 }, { autoAlpha: 1, y: 0, duration: 0.15 }, 0.5)
    },
    root,
  )
})

onUnmounted(() => animations?.revert())
</script>

<template>
  <div ref="story" class="story">
    <div class="visual" aria-hidden="true">
      <img :src="heroImage" alt="" />
      <img class="side-image" :src="menuImage" alt="" />
    </div>

    <header class="hero-title">
      <h1 class="font-display text-6xl sm:text-8xl">Friendsgiving Day</h1>
    </header>

    <main class="menu menu-items">
      <h2 class="mb-8 font-serif text-4xl text-center">The Menu</h2>

      <div class="flex flex-col gap-6">
        <MenuItem title="Mashed Potatoes" subtitle="with Herbs and Gravy" />
        <MenuItem title="Cajun Seasoned Turkey Breast" />
        <MenuItem title="Glazed Ham" />
        <MenuItem
          title="Green Bean Casserole"
          subtitle="a casserole of Fresh Green Beans, Cream of Chicken Soup, Fried Onions, and Seasonings"
        />
        <MenuItem
          title="Macaroni and Cheese with Bacon"
          subtitle="sharp white cheddar and gruyere infused with a shallot and sage oil"
        />
        <MenuItem
          title="Sweet Potato Casserole"
          subtitle="a casserole of mashed yams, butter, brown sugar, topped with marshmallows toasted lightly"
        />
      </div>
    </main>
  </div>
  <!--
  <div class="grid min-h-dvh grid-cols-1 gap-8 lg:grid-cols-12">
    <div class="relative min-h-64 overflow-hidden lg:col-span-4">
      <img
        src="@/assets/thanksgiving dinner table.jpg"
        alt="A dinner table topped with traditional Thanksgiving fare"
        class="absolute insert-0 h-full w-full object-cover"
      />
    </div>
    <section class="min-w-0 px-6 py-8 lg:col-span-8 lg:px-12">
      <div><h2 class="font-display text-9xl text-center mb-4">Friendsgiving Day</h2></div>
      <div class="flex flex-col gap-6">
        <MenuItem title="Mashed Potatoes" subtitle="with Herbs and Gravy" />
        <MenuItem title="Cajun Seasoned Turkey Breast" />
        <MenuItem title="Glazed Ham" />
        <MenuItem
          title="Green Bean Casserole"
          subtitle="a casserole of Fresh Green Beans, Cream of Chicken Soup, Fried Onions, and Seasonings"
        />
        <MenuItem
          title="Macaroni and Cheese with Bacon"
          subtitle="sharp white cheddar and gruyere infused with a shallot and sage oil"
        />
        <MenuItem
          title="Sweet Potato Casserole"
          subtitle="a casserole of mashed yams, butter, brown sugar, topped with marshmallows allowed to toast lightly"
        />
      </div>
    </section>
  </div> -->

  <!-- <RouterView /> -->
</template>

<style scoped>
.story {
  position: relative;
  isolation: isolate;
}

.visual {
  position: relative;
  height: 40svh;
}

.visual img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.side-image {
  opacity: 0;
}

.hero-title,
.menu {
  padding: 3rem 1.5rem;
}

@media (min-width: 64rem) and (prefers-reduced-motion: no-preference) {
  .visual {
    position: sticky;
    top: 0;
    height: 100dvh;
    margin-bottom: -100dvh;
    z-index: -1;
    pointer-events: none;
  }

  .hero-title {
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100dvh;
    text-align: center;
    color: white;
    background: rgb(0 0 0 / 35%);
  }

  .menu {
    margin-left: 33.333%;
    min-height: 100dvh;
    padding: 4rem;
  }
}
</style>
