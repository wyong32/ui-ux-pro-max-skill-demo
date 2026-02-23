<script setup>
const routes = Array.from({ length: 9 }, (_, i) => ({ id: i + 1, name: `Route ${i + 1}` }))

const quickLinks = [
  { name: '强度榜', desc: 'Tier List 与推荐阵容', path: '#tier', icon: 'tier' },
  { name: 'Boss 攻略', desc: '各路线传说 Boss 打法', path: '#boss', icon: 'boss' },
  { name: 'Wiki', desc: '图鉴、道具与地图', path: '#wiki', icon: 'wiki' },
]
</script>

<template>
  <div class="min-h-screen bg-slate-950 text-slate-100">
    <!-- 浮动导航 - ui-ux-pro-max: top-4 left-4 right-4 -->
    <nav
      class="fixed top-4 left-4 right-4 z-50 mx-auto flex max-w-6xl items-center justify-between rounded-2xl border border-slate-700/60 bg-slate-900/90 px-6 py-3 backdrop-blur-md transition-colors duration-200"
      role="navigation"
    >
      <a href="/" class="font-display text-lg font-bold tracking-wide text-amber-400 transition-colors duration-200 hover:text-amber-300">
        PokéPath TD
      </a>
      <div class="flex items-center gap-6">
        <a href="#routes" class="text-sm text-slate-300 transition-colors duration-200 hover:text-white cursor-pointer">路线</a>
        <a href="#tier" class="text-sm text-slate-300 transition-colors duration-200 hover:text-white cursor-pointer">强度榜</a>
        <a href="#quick" class="text-sm text-slate-300 transition-colors duration-200 hover:text-white cursor-pointer">攻略</a>
      </div>
    </nav>

    <!-- Hero -->
    <header class="relative overflow-hidden px-4 pt-32 pb-24 md:pt-40 md:pb-32">
      <div class="absolute inset-0 bg-[radial-gradient(ellipse_80%_60%_at_50%_-20%,rgba(251,191,36,0.12),transparent)]" aria-hidden="true" />
      <div class="relative mx-auto max-w-5xl text-center">
        <h1 class="font-display text-4xl font-extrabold tracking-tight text-white drop-shadow-sm md:text-6xl">
          PokéPath TD
          <span class="block text-amber-400">攻略站</span>
        </h1>
        <p class="mx-auto mt-6 max-w-2xl text-lg text-slate-400">
          九条路线、传说 Boss、进化与阵容——一站式塔防攻略与强度参考。
        </p>
        <div class="mt-10 flex flex-wrap items-center justify-center gap-4">
          <a
            href="https://pokepath.gg/en/play"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center gap-2 rounded-xl bg-amber-500 px-6 py-3 font-semibold text-slate-900 shadow-lg transition-colors duration-200 hover:bg-amber-400 cursor-pointer focus:outline-none focus:ring-2 focus:ring-amber-400 focus:ring-offset-2 focus:ring-offset-slate-950"
          >
            <svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" aria-hidden="true">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z" />
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
            去玩游戏
          </a>
          <a
            href="#routes"
            class="inline-flex items-center gap-2 rounded-xl border border-slate-600 bg-slate-800/80 px-6 py-3 font-semibold text-slate-200 transition-colors duration-200 hover:border-slate-500 hover:bg-slate-700/80 cursor-pointer"
          >
            查阅攻略
          </a>
        </div>
      </div>
    </header>

    <!-- 路线 1–9 -->
    <section id="routes" class="px-4 pb-20 pt-6">
      <div class="mx-auto max-w-6xl">
        <h2 class="font-display mb-8 text-2xl font-bold text-white md:text-3xl">九条路线</h2>
        <div class="grid grid-cols-2 gap-3 sm:grid-cols-3 md:gap-4 lg:grid-cols-5">
          <a
            v-for="r in routes"
            :key="r.id"
            :href="`#route-${r.id}`"
            class="group flex flex-col rounded-2xl border border-slate-700/60 bg-slate-800/60 p-5 transition-colors duration-200 hover:border-amber-500/50 hover:bg-slate-800 cursor-pointer focus:outline-none focus:ring-2 focus:ring-amber-400 focus:ring-offset-2 focus:ring-offset-slate-950"
          >
            <span class="text-slate-400 transition-colors duration-200 group-hover:text-amber-400">路线</span>
            <span class="font-display text-2xl font-bold text-white">{{ r.id }}</span>
            <span class="mt-1 text-sm text-slate-500">地图 · Boss</span>
          </a>
        </div>
      </div>
    </section>

    <!-- 快捷入口 -->
    <section id="quick" class="px-4 pb-12 pt-8">
      <div class="mx-auto max-w-6xl">
        <h2 class="font-display mb-8 text-2xl font-bold text-white md:text-3xl">攻略入口</h2>
        <div class="grid gap-4 md:grid-cols-3">
          <a
            v-for="link in quickLinks"
            :key="link.name"
            :href="link.path"
            class="group flex items-start gap-4 rounded-2xl border border-slate-700/60 bg-slate-800/60 p-6 transition-colors duration-200 hover:border-cyan-500/50 hover:bg-slate-800 cursor-pointer"
          >
            <span
              class="flex h-12 w-12 shrink-0 items-center justify-center rounded-xl bg-slate-700/80 text-cyan-400 transition-colors duration-200 group-hover:bg-cyan-500/20"
              aria-hidden="true"
            >
              <svg v-if="link.icon === 'tier'" class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
              </svg>
              <svg v-else-if="link.icon === 'boss'" class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />
              </svg>
              <svg v-else class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" />
              </svg>
            </span>
            <div>
              <h3 class="font-display font-semibold text-white">{{ link.name }}</h3>
              <p class="mt-1 text-sm text-slate-400">{{ link.desc }}</p>
            </div>
          </a>
        </div>
      </div>
    </section>

    <!-- 强度榜 / Boss / Wiki 锚点区 -->
    <section id="tier" class="scroll-mt-24 border-t border-slate-800/80 px-4 py-12">
      <div class="mx-auto max-w-6xl">
        <h2 class="font-display text-xl font-bold text-white">强度榜 Tier List</h2>
        <p class="mt-2 text-slate-400">推荐宝可梦与阵容将在此展示（后续页面）。</p>
      </div>
    </section>
    <section id="boss" class="scroll-mt-24 px-4 py-12">
      <div class="mx-auto max-w-6xl">
        <h2 class="font-display text-xl font-bold text-white">Boss 攻略</h2>
        <p class="mt-2 text-slate-400">各路线传说 Boss 打法要点（后续页面）。</p>
      </div>
    </section>
    <section id="wiki" class="scroll-mt-24 px-4 py-12">
      <div class="mx-auto max-w-6xl">
        <h2 class="font-display text-xl font-bold text-white">Wiki</h2>
        <p class="mt-2 text-slate-400">图鉴、道具与地图（后续页面）。</p>
      </div>
    </section>

    <!-- Footer -->
    <footer class="border-t border-slate-800 px-4 py-8">
      <div class="mx-auto max-w-6xl flex flex-col items-center justify-between gap-4 text-sm text-slate-500 md:flex-row">
        <span>PokéPath TD 为第三方攻略站，非官方。</span>
        <a
          href="https://pokepath.gg/"
          target="_blank"
          rel="noopener noreferrer"
          class="transition-colors duration-200 hover:text-amber-400 cursor-pointer"
        >
          官方站点 pokepath.gg
        </a>
      </div>
    </footer>
  </div>
</template>
