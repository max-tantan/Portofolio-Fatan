<script setup>
import { RouterLink, RouterView, useRoute } from 'vue-router'

const route = useRoute()

const navigation = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Skills', path: '/skills' },
  { name: 'Project', path: '/project' },
  { name: 'Contact', path: '/contact' },
]
</script>

<template>
  <div class="min-h-screen bg-stone-950 text-stone-100">
    <div class="pointer-events-none fixed inset-0 -z-10 overflow-hidden">
      <div class="ambient-orb absolute inset-x-0 top-0 h-72 bg-[radial-gradient(circle_at_top,_rgba(245,158,11,0.18),_transparent_55%)]"></div>
      <div class="ambient-orb ambient-orb-delay absolute bottom-0 left-1/2 h-80 w-80 -translate-x-1/2 rounded-full bg-white/5 blur-3xl"></div>
      <div class="grid-pattern absolute inset-0 opacity-40"></div>
    </div>

    <div class="mx-auto flex min-h-screen max-w-7xl flex-col px-4 pb-10 pt-6 sm:px-6 lg:px-8">
      <!-- App header / navigation -->
      <header class="sticky top-4 z-20 mb-8">
        <div class="surface flex items-center justify-between rounded-full px-5 py-3">
          <RouterLink to="/" class="flex items-center gap-3">
            <span class="flex h-10 w-10 items-center justify-center rounded-full bg-amber-300 text-sm font-semibold text-stone-950">
              FA
            </span>
            <div>
              <p class="text-sm font-semibold tracking-[0.24em] text-stone-200 uppercase">Portfolio</p>
              <p class="text-xs text-stone-400">Student portfolio and creative journey</p>
            </div>
          </RouterLink>

          <nav class="hidden items-center gap-2 md:flex">
            <RouterLink
              v-for="item in navigation"
              :key="item.path"
              :to="item.path"
              class="rounded-full px-4 py-2 text-sm text-stone-300 transition hover:bg-white/10 hover:text-white"
              :class="route.path === item.path ? 'bg-white text-stone-950' : 'bg-transparent'"
            >
              {{ item.name }}
            </RouterLink>
          </nav>
        </div>

        <nav class="mt-3 flex gap-2 overflow-x-auto md:hidden">
          <RouterLink
            v-for="item in navigation"
            :key="`${item.path}-mobile`"
            :to="item.path"
            class="surface shrink-0 rounded-full px-4 py-2 text-sm text-stone-300 transition hover:bg-white/10 hover:text-white"
            :class="route.path === item.path ? 'bg-white text-stone-950' : 'bg-transparent'"
          >
            {{ item.name }}
          </RouterLink>
        </nav>
      </header>

      <main class="flex-1">
        <RouterView v-slot="{ Component, route: currentRoute }">
          <Transition name="page-slide" mode="out-in">
            <component :is="Component" :key="currentRoute.fullPath" />
          </Transition>
        </RouterView>
      </main>

      <!-- App footer -->
      <footer class="mt-12 border-t border-white/10 pt-6 text-sm text-stone-400">
        <div class="flex flex-col gap-2 sm:flex-row sm:items-center sm:justify-between">
          <p>Built as a job-ready portfolio with clear strengths, selected projects, and contact points.</p>
          <p>Frontend portfolio template for applications, networking, and freelance outreach.</p>
        </div>
      </footer>
    </div>
  </div>
</template>
