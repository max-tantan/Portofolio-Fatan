<script setup>
import { RouterLink } from 'vue-router'
import RevealBlock from '../components/RevealBlock.vue'
import { albumWorks } from '../data/Data'
</script>

<template>
  <section class="space-y-8">
    <!-- Album hero section -->
    <RevealBlock as="div" :delay="40" class="album-shell rounded-[2.5rem] p-7 sm:p-10">
      <div class="flex flex-col gap-6 lg:flex-row lg:items-end lg:justify-between">
        <div class="max-w-3xl">
          <p class="text-sm uppercase tracking-[0.28em] text-amber-300">Creative album</p>
          <h1 class="mt-4 text-4xl font-semibold leading-tight text-white sm:text-5xl lg:text-6xl">
            Poster, photo, and visual editing collected in one playful gallery.
          </h1>
          <p class="mt-5 max-w-2xl text-base leading-8 text-stone-300">
            Halaman ini dibuat khusus untuk karya visual. Gayanya lebih eksperimental dari halaman lain,
            dengan gallery yang bisa digeser dan card yang terasa seperti kumpulan karya di meja kreatif.
          </p>
        </div>

        <div class="flex flex-col gap-3 sm:flex-row">
          <RouterLink to="/project" class="btn-secondary">
            Back to Projects
          </RouterLink>
          <a href="mailto:fatannurrizqi@gmail.com?subject=Album%20Portfolio" class="btn-primary">
            Request Full Portfolio
          </a>
        </div>
      </div>
    </RevealBlock>

    <!-- Album scroller section -->
    <RevealBlock as="section" :delay="100" class="space-y-4">
      <div class="flex items-center justify-between gap-4">
        <div>
          <p class="text-sm uppercase tracking-[0.22em] text-stone-400">Swipe gallery</p>
          <h2 class="mt-2 text-2xl font-semibold text-white">Geser untuk menjelajahi karya visual.</h2>
        </div>
        <p class="hidden text-sm text-stone-500 md:block">Drag, swipe, atau scroll ke samping.</p>
      </div>

      <div class="album-scroller">
        <article
          v-for="(work, index) in albumWorks"
          :key="work.title"
          class="album-card"
          :class="[`album-${work.size}`, `album-rotate-${(index % 4) + 1}`]"
        >
          <div class="album-frame">
            <div class="album-art" :class="`bg-gradient-to-br ${work.palette}`">
              <div class="album-art-overlay"></div>
              <div class="album-art-lines"></div>
              <div class="album-art-copy">
                <p class="text-xs uppercase tracking-[0.3em] text-white/70">{{ work.type }}</p>
                <h3 class="mt-3 text-2xl font-semibold text-white sm:text-3xl">{{ work.title }}</h3>
              </div>
            </div>

            <div class="album-meta">
              <div class="flex items-center justify-between gap-4">
                <span class="album-pill">{{ work.type }}</span>
                <span class="text-xs uppercase tracking-[0.2em] text-stone-500">2025</span>
              </div>
              <p class="mt-4 text-sm leading-7 text-stone-300">
                {{ work.note }}
              </p>
            </div>
          </div>
        </article>
      </div>
    </RevealBlock>

    <!-- Album spotlight section -->
    <div class="grid gap-6 lg:grid-cols-[0.9fr_1.1fr]">
      <RevealBlock as="article" :delay="120" class="surface rounded-[2rem] p-7 sm:p-8">
        <p class="text-sm uppercase tracking-[0.22em] text-stone-400">Creative direction</p>
        <h2 class="mt-3 text-3xl font-semibold text-white">Visual work yang lebih bebas, ekspresif, dan tetap terstruktur.</h2>
        <p class="mt-4 text-base leading-8 text-stone-300">
          Berbeda dari halaman portfolio utama yang cenderung tenang, bagian album ini sengaja dibuat lebih playful
          agar karakter karya poster, foto, dan video editing bisa terasa lebih hidup.
        </p>
      </RevealBlock>

      <RevealBlock as="article" :delay="200" class="album-board rounded-[2rem] p-7 sm:p-8">
        <p class="text-sm uppercase tracking-[0.22em] text-amber-300">Creative notes</p>
        <div class="mt-6 grid gap-4 md:grid-cols-2">
          <div class="album-note rotate-[-2deg]">
            <p class="text-xs uppercase tracking-[0.18em] text-stone-600">Focus</p>
            <p class="mt-3 text-base leading-7 text-stone-800">Poster design, social media visual, photo retouch, dan video mood editing.</p>
          </div>
          <div class="album-note rotate-[2deg]">
            <p class="text-xs uppercase tracking-[0.18em] text-stone-600">Style</p>
            <p class="mt-3 text-base leading-7 text-stone-800">Bold typography, kontras warna, layout eksploratif, dan framing yang komunikatif.</p>
          </div>
          <div class="album-note rotate-[1deg]">
            <p class="text-xs uppercase tracking-[0.18em] text-stone-600">Use case</p>
            <p class="mt-3 text-base leading-7 text-stone-800">Cocok untuk event poster, social campaign, promosi sekolah, dan portfolio kreatif.</p>
          </div>
          <div class="album-note rotate-[-1deg]">
            <p class="text-xs uppercase tracking-[0.18em] text-stone-600">Next step</p>
            <p class="mt-3 text-base leading-7 text-stone-800">Nanti kita bisa ganti card ini dengan gambar asli karya kamu supaya album terasa lebih personal.</p>
          </div>
        </div>
      </RevealBlock>
    </div>
  </section>
</template>
