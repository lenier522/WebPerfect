<template>
  <div :class="['min-h-screen font-sans antialiased', themeClass]" >
    <!-- HEADER -->
    <header class="sticky top-0 z-50 bg-white/50 dark:bg-black/50 backdrop-blur border-b border-gray-100 dark:border-[#0b0b0b]">
      <div class="max-w-7xl mx-auto px-6 lg:px-8 h-16 flex items-center justify-between">
        <a href="/" class="flex items-center gap-3" aria-label="Inicio - WebPerf³ct">
          <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-[#6d28d9] to-[#06b6d4] flex items-center justify-center text-white font-extrabold shadow">
            WP
          </div>
          <div class="leading-tight">
            <div class="text-sm font-semibold">WebPerf³ct</div>
            <div class="text-xs text-[#6b6b67] dark:text-[#9f9f9d] -mt-0.5">Marketing & Software</div>
          </div>
        </a>

        <div class="hidden lg:flex items-center gap-6">
          <a href="#projects" class="text-sm hover:underline">Proyectos</a>
          <a href="#services" class="text-sm hover:underline">Servicios</a>
          <a href="#about" class="text-sm hover:underline">Nosotros</a>
        </div>

        <div class="flex items-center gap-2">
          <!-- Search quick -->
          <div class="hidden md:flex items-center bg-gray-100 dark:bg-white/6 rounded-full px-3 py-1 gap-2">
            <svg class="w-4 h-4 text-gray-500" viewBox="0 0 24 24" fill="none"><path d="M11 19a8 8 0 1 1 5.293-14.293A8 8 0 0 1 11 19z" stroke="currentColor" stroke-width="1.4"/></svg>
            <input v-model="searchTerm" @keydown.enter.prevent="focusProjects" aria-label="Buscar proyectos" placeholder="Buscar proyectos..." class="bg-transparent text-sm outline-none w-40" />
          </div>

          <!-- Theme toggle -->
          <button @click="toggleTheme" :aria-pressed="isDark.toString()" class="p-2 rounded-md hover:bg-gray-100 dark:hover:bg-white/5" :title="isDark ? 'Cambiar a tema claro' : 'Cambiar a tema oscuro'">
            <svg v-if="isDark" class="w-5 h-5" viewBox="0 0 24 24" fill="none"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
            <svg v-else class="w-5 h-5" viewBox="0 0 24 24" fill="none"><path d="M12 3v1M12 20v1M4.2 4.2l.7.7M18.1 18.1l.7.7M1 12h1M22 12h1M4.2 19.8l.7-.7M18.1 5.9l.7-.7" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/></svg>
          </button>

          <!-- Auth buttons (clases EXACTAS que pediste) -->
          <a
            href="/login"
            class="inline-block rounded-sm border border-transparent px-4 py-1 text-sm leading-normal text-[#1b1b18] hover:border-[#19140035] dark:text-[#EDEDEC] dark:hover:border-[#3E3E3A]"
          >
            Log in
          </a>
          <a
            href="/register"
            class="inline-block rounded-sm border border-[#19140035] px-4 py-1 text-sm leading-normal text-[#1b1b18] hover:border-[#1915014a] dark:border-[#3E3E3A] dark:text-[#EDEDEC] dark:hover:border-[#62605b]"
          >
            Register
          </a>

          <!-- mobile menu -->
          <button @click="mobileOpen = !mobileOpen" class="lg:hidden p-2 ml-1 rounded-md" :aria-expanded="String(mobileOpen)" aria-label="Abrir menú">
            <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none">
              <path v-if="!mobileOpen" d="M4 6h16M4 12h16M4 18h16" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
              <path v-else d="M6 6l12 12M6 18L18 6" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
            </svg>
          </button>
        </div>
      </div>

      <div v-if="mobileOpen" class="lg:hidden border-t border-gray-100 dark:border-[#0b0b0b]">
        <div class="px-6 py-4 flex flex-col gap-3">
          <a href="#projects" class="text-sm">Proyectos</a>
          <a href="#services" class="text-sm">Servicios</a>
          <a href="#about" class="text-sm">Nosotros</a>
          <a href="#contact" class="text-sm">Contacto</a>
        </div>
      </div>
    </header>

    <!-- HERO: creativo, con mockup y CTA -->
    <main>
      <section class="relative overflow-hidden">
        <div class="max-w-7xl mx-auto px-6 lg:px-8 grid grid-cols-1 lg:grid-cols-12 gap-10 items-center py-20 lg:py-28">
          <!-- Left: copy -->
          <div class="lg:col-span-7 space-y-6">
            <div class="inline-flex items-center gap-3 bg-[#f1f5f9] dark:bg-white/5 px-3 py-1 rounded-full text-xs font-medium text-[#0b6b4f] w-max">
              Tecnología · Marketing · Productos
            </div>

            <h1 class="text-3xl sm:text-4xl lg:text-5xl font-extrabold leading-tight">
              Diseñamos, construimos y promocionamos software que escala negocios
            </h1>

            <p class="text-lg text-[#4b4b47] dark:text-[#cfcfcf] max-w-2xl leading-relaxed">
              E-commerce (Bagisto), CRM (Krayin), ERP (Aureus) y apps en Flutter. Experiencia end-to-end: producto, arquitectura, growth y operaciones.
            </p>

            <div class="flex flex-wrap gap-3 items-center">
              <a href="#projects" class="inline-flex items-center gap-3 rounded-full bg-[#7c3aed] text-white px-5 py-3 font-semibold shadow hover:brightness-95 transition">
                Ver proyectos
              </a>

              <a href="/contact" class="inline-flex items-center gap-2 px-4 py-2 rounded-md border border-gray-200 dark:border-[#222] text-sm">
                Solicitar demo
              </a>

              <a
                href="/register"
                class="inline-block rounded-sm border border-[#19140035] px-5 py-1.5 text-sm leading-normal text-[#1b1b18] hover:border-[#1915014a] dark:border-[#3E3E3A] dark:text-[#EDEDEC] dark:hover:border-[#62605b]"
              >
                Register
              </a>
            </div>

            <!-- UX quick controls: search, view, sort -->
            <div class="mt-6 flex flex-col sm:flex-row sm:items-center gap-3">
              <div class="flex items-center gap-2 bg-gray-100 dark:bg-white/6 rounded-full px-3 py-1">
                <svg class="w-4 h-4 text-gray-500" viewBox="0 0 24 24" fill="none"><path d="M11 19a8 8 0 1 1 5.293-14.293A8 8 0 0 1 11 19z" stroke="currentColor" stroke-width="1.4"/></svg>
                <input v-model="searchTerm" placeholder="Buscar proyectos, tecnología o etiquetas..." class="bg-transparent outline-none text-sm w-64" aria-label="Buscar proyectos" />
                <button @click="searchTerm = ''" v-if="searchTerm" class="text-xs px-2">Limpiar</button>
              </div>

              <div class="ml-auto flex items-center gap-2">
                <label class="text-xs text-[#6b6b67] dark:text-[#9f9f9d]">Vista</label>
                <div role="tablist" class="inline-flex bg-gray-100 dark:bg-white/6 rounded-full p-1">
                  <button @click="viewMode = 'grid'" :aria-pressed="viewMode === 'grid'" class="px-3 py-1 rounded-full text-sm" :class="viewMode === 'grid' ? 'bg-[#7c3aed] text-white' : ''" title="Vista en cuadrícula">Grid</button>
                  <button @click="viewMode = 'list'" :aria-pressed="viewMode === 'list'" class="px-3 py-1 rounded-full text-sm" :class="viewMode === 'list' ? 'bg-[#7c3aed] text-white' : ''" title="Vista en lista">Lista</button>
                </div>

                <label class="text-xs text-[#6b6b67] dark:text-[#9f9f9d]">Orden</label>
                <select v-model="sortBy" class="text-sm rounded-md bg-white dark:bg-[#071010] border border-gray-200 dark:border-[#111] px-2 py-1">
                  <option value="featured">Destacados</option>
                  <option value="newest">Más recientes</option>
                  <option value="alpha">A → Z</option>
                </select>
              </div>
            </div>
          </div>

          <!-- Right: device mockup + gallery -->
          <div class="lg:col-span-5">
            <div class="rounded-3xl shadow-2xl overflow-hidden border border-gray-100 dark:border-[#0f0f0f] bg-white dark:bg-[#071010]">
              <div class="p-4">
                <div class="relative rounded-xl overflow-hidden aspect-[9/16] bg-gray-50 dark:bg-[#061414] flex items-stretch">
                  <!-- phone mockup left with image -->
                  <div class="w-full">
                    <img :src="mockupImage" alt="Mockup app" class="w-full h-full object-cover" loading="lazy" />
                  </div>
                </div>

                <div class="mt-4 flex items-center justify-between">
                  <div>
                    <div class="text-xs text-[#6b6b67] dark:text-[#cfcfcf]">Highlights</div>
                    <div class="text-lg font-semibold">Bagisto · Omni-channel</div>
                  </div>

                  <div class="flex items-center gap-3">
                    <button @click="openProjectModal(projects[0])" class="rounded-md px-4 py-2 bg-[#7c3aed] text-white text-sm shadow hover:brightness-95">Ver caso</button>
                    <a href="/contact" class="rounded-md px-3 py-2 border border-gray-200 dark:border-[#111] text-sm">Contacto</a>
                  </div>
                </div>

                <div class="mt-4 grid grid-cols-3 gap-2">
                  <img v-for="(t, i) in thumbs" :key="i" :src="t" class="w-full h-20 object-cover rounded-lg" :alt="'Thumb ' + i" loading="lazy" />
                </div>
              </div>
            </div>

            <!-- badges -->
            <div class="mt-4 grid grid-cols-2 gap-3">
              <div class="p-3 bg-white dark:bg-[#081010] border border-gray-100 dark:border-[#111] rounded-xl flex items-center gap-3">
                <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/laravel/laravel-plain.svg" alt="Laravel" class="w-6 h-6" />
                <div>
                  <div class="text-xs text-[#6b6b67] dark:text-[#9f9f9d]">Backend</div>
                  <div class="text-sm font-semibold">Laravel</div>
                </div>
              </div>
              <div class="p-3 bg-white dark:bg-[#081010] border border-gray-100 dark:border-[#111] rounded-xl flex items-center gap-3">
                <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/flutter/flutter-original.svg" alt="Flutter" class="w-6 h-6" />
                <div>
                  <div class="text-xs text-[#6b6b67] dark:text-[#9f9f9d]">Mobile</div>
                  <div class="text-sm font-semibold">Flutter</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- PROJECTS section with grid/list toggles and no overlapping text -->
      <section id="projects" class="max-w-7xl mx-auto px-6 lg:px-8 py-12">
        <div class="mb-6 flex items-center justify-between gap-6">
          <div>
            <h2 class="text-2xl font-bold">Proyectos & Software</h2>
            <p class="text-sm text-[#6b6b67] dark:text-[#9f9f9d]">Filtra, busca y cambia la vista. UX pensada para encontrar proyectos rápido.</p>
          </div>

          <div class="flex items-center gap-3">
            <div class="flex items-center gap-2 bg-gray-100 dark:bg-white/5 rounded-full px-3 py-1 text-xs">
              <button v-for="f in filters" :key="f" @click="selectedFilter = f" :aria-pressed="selectedFilter === f"
                :class="['px-3 py-1 rounded-full text-sm', selectedFilter === f ? 'bg-[#7c3aed] text-white' : 'text-[#444] dark:text-[#cfcfcf]']">
                {{ f }}
              </button>
            </div>
          </div>
        </div>

        <!-- Grid Mode -->
        <div v-if="viewMode === 'grid'" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
          <article v-for="p in sortedFilteredProjects" :key="p.id" class="group bg-white dark:bg-[#081010] border border-gray-100 dark:border-[#111] rounded-2xl overflow-hidden shadow-sm transform hover:-translate-y-1 transition">
            <div class="relative aspect-[16/10] bg-gray-100 dark:bg-[#061414]">
              <img :src="p.image" :alt="p.title" class="w-full h-full object-cover" loading="lazy" />
              <div class="absolute inset-0 bg-gradient-to-t from-black/25 to-transparent"></div>

              <div class="absolute left-4 bottom-4 text-white">
                <div class="text-lg font-semibold">{{ p.title }}</div>
                <div class="text-xs text-white/80">{{ p.type }}</div>
              </div>

              <div class="absolute right-4 top-4 flex gap-2">
                <span v-for="t in p.tags" :key="t" class="text-xs bg-white/70 dark:bg-white/10 px-2 py-1 rounded-md">{{ t }}</span>
              </div>
            </div>

            <div class="p-4">
              <p class="text-sm text-[#4b4b47] dark:text-[#cfcfcf] mb-3 leading-relaxed">{{ p.description }}</p>

              <div class="flex items-center justify-between">
                <div class="text-xs text-[#6b6b67] dark:text-[#9f9f9d]">{{ p.year }}</div>
                <div class="flex items-center gap-2">
                  <button @click="openProjectModal(p)" class="text-sm px-3 py-1 rounded-md border border-gray-200 dark:border-[#161616]">Ver</button>
                  <a v-if="p.demo" :href="p.demo" target="_blank" rel="noopener" class="text-sm px-3 py-1 rounded-md bg-[#7c3aed] text-white">Demo</a>
                </div>
              </div>
            </div>
          </article>
        </div>

        <!-- List Mode -->
        <div v-else class="flex flex-col gap-4">
          <div v-for="p in sortedFilteredProjects" :key="p.id" class="flex items-stretch gap-4 bg-white dark:bg-[#081010] border border-gray-100 dark:border-[#111] rounded-2xl p-4">
            <div class="w-40 min-w-[160px] rounded-lg overflow-hidden bg-gray-100 dark:bg-[#061414]">
              <img :src="p.image" :alt="p.title" class="w-full h-28 object-cover" loading="lazy" />
            </div>
            <div class="flex-1">
              <div class="flex items-start justify-between gap-4">
                <div>
                  <div class="text-lg font-semibold">{{ p.title }}</div>
                  <div class="text-xs text-[#6b6b67] dark:text-[#9f9f9d]">{{ p.type }} • {{ p.year }}</div>
                </div>
                <div class="flex items-center gap-2">
                  <a v-if="p.demo" :href="p.demo" target="_blank" rel="noopener" class="text-sm px-3 py-1 rounded-md bg-[#7c3aed] text-white">Demo</a>
                  <button @click="openProjectModal(p)" class="text-sm px-3 py-1 rounded-md border border-gray-200 dark:border-[#161616]">Ver</button>
                </div>
              </div>

              <p class="text-sm text-[#4b4b47] dark:text-[#cfcfcf] mt-2 leading-relaxed">{{ p.description }}</p>
              <div class="mt-3 flex items-center gap-2 text-xs text-[#6b6b67] dark:text-[#9f9f9d]">
                <span v-for="s in p.stack" :key="s" class="px-2 py-1 bg-gray-100 dark:bg-white/5 rounded-md">{{ s }}</span>
              </div>
            </div>
          </div>
        </div>

      </section>

      <!-- Services / About -->
      <section id="services" class="bg-gray-50 dark:bg-[#071010] py-12">
        <div class="max-w-7xl mx-auto px-6 lg:px-8 grid grid-cols-1 lg:grid-cols-3 gap-8">
          <div class="lg:col-span-1">
            <h3 class="text-xl font-semibold">Cómo trabajamos</h3>
            <p class="text-sm text-[#6b6b67] dark:text-[#9f9f9d]">Producto, engineering y growth — en un mismo equipo con objetivos claros.</p>
          </div>

          <div class="lg:col-span-2 grid grid-cols-1 md:grid-cols-2 gap-6">
            <div class="p-6 bg-white dark:bg-[#081010] border border-gray-100 dark:border-[#111] rounded-2xl">
              <h4 class="font-semibold mb-2">Estrategia de producto</h4>
              <p class="text-sm text-[#5b5b57] dark:text-[#bdbdbd]">Discovery, validación y roadmap con métricas OKR/ KPI.</p>
            </div>

            <div class="p-6 bg-white dark:bg-[#081010] border border-gray-100 dark:border-[#111] rounded-2xl">
              <h4 class="font-semibold mb-2">Ingeniería & Integraciones</h4>
              <p class="text-sm text-[#5b5b57] dark:text-[#bdbdbd]">Arquitectura escalable, API-first y despliegues automáticos.</p>
            </div>

            <div class="p-6 bg-white dark:bg-[#081010] border border-gray-100 dark:border-[#111] rounded-2xl">
              <h4 class="font-semibold mb-2">Growth & Performance</h4>
              <p class="text-sm text-[#5b5b57] dark:text-[#bdbdbd]">Experimentación, CRO y campañas data-driven.</p>
            </div>

            <div class="p-6 bg-white dark:bg-[#081010] border border-gray-100 dark:border-[#111] rounded-2xl">
              <h4 class="font-semibold mb-2">Soporte & Operaciones</h4>
              <p class="text-sm text-[#5b5b57] dark:text-[#bdbdbd]">Monitoreo, SRE y acuerdos SLA.</p>
            </div>
          </div>
        </div>
      </section>

      <!-- Testimonials -->
      <section id="about" class="max-w-7xl mx-auto px-6 lg:px-8 py-12">
        <h3 class="text-xl font-semibold mb-6">Testimonios</h3>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <blockquote v-for="(t, i) in testimonials" :key="i" class="p-6 bg-white dark:bg-[#081010] border border-gray-100 dark:border-[#111] rounded-2xl">
            <p class="text-sm text-[#333] dark:text-[#d9d9d9]">“{{ t.quote }}”</p>
            <footer class="mt-4 flex items-center gap-3">
              <img :src="t.avatar" :alt="t.name" class="w-10 h-10 rounded-full object-cover" loading="lazy" />
              <div>
                <div class="text-sm font-semibold">{{ t.name }}</div>
                <div class="text-xs text-[#6b6b67] dark:text-[#9f9f9d]">{{ t.role }}</div>
              </div>
            </footer>
          </blockquote>
        </div>
      </section>

      <!-- final CTA -->
      <section id="contact" class="max-w-7xl mx-auto px-6 lg:px-8 py-12">
        <div class="rounded-2xl p-8 bg-gradient-to-r from-white to-[#f8fafc] dark:from-[#071010] dark:to-[#041010] border border-gray-100 dark:border-[#111] shadow-xl flex flex-col lg:flex-row items-center justify-between gap-6">
          <div>
            <h3 class="text-2xl font-semibold">¿Listo para lanzar tu producto?</h3>
            <p class="text-sm text-[#6b6b67] dark:text-[#9f9f9d]">Agendemos una consultoría y te damos una estimación de 48 horas.</p>
          </div>

          <div class="flex gap-3">
            <a href="/contact" class="rounded-md px-5 py-3 bg-[#7c3aed] text-white font-semibold">Agendar consultoría</a>
            <a href="/contact" class="rounded-md px-5 py-3 border border-gray-200 dark:border-[#111]">Enviar brief</a>
          </div>
        </div>
      </section>

    </main>

    <!-- FOOTER -->
    <footer class="border-t border-gray-100 dark:border-[#121210] bg-white/50 dark:bg-transparent">
      <div class="max-w-7xl mx-auto px-6 lg:px-8 py-8 flex flex-col md:flex-row items-center justify-between gap-6">
        <div class="flex items-center gap-3">
          <div class="w-9 h-9 rounded-md bg-gradient-to-br from-[#7c3aed] to-[#06b6d4] text-white flex items-center justify-center font-bold">WP</div>
          <div>
            <div class="font-semibold">WebPerf³ct</div>
            <div class="text-xs text-[#6b6b67] dark:text-[#9f9f9d]">Agencia & Desarrollo</div>
          </div>
        </div>

        <div class="text-sm text-[#6b6b67] dark:text-[#9f9f9d]">© {{ new Date().getFullYear() }} WebPerf³ct — Todos los derechos reservados</div>

        <nav class="flex items-center gap-4 text-sm text-[#6b6b67] dark:text-[#9f9f9d]">
          <a href="/privacy" class="hover:underline">Privacidad</a>
          <a href="/terms" class="hover:underline">Términos</a>
          <a href="/contact" class="hover:underline">Contacto</a>
        </nav>
      </div>
    </footer>

    <!-- MODAL -->
    <div v-if="modalOpen" class="fixed inset-0 z-60 flex items-center justify-center p-4">
      <div class="absolute inset-0 bg-black/50" @click="closeModal" aria-hidden="true"></div>

      <div role="dialog" aria-modal="true" class="relative z-10 max-w-4xl w-full rounded-2xl overflow-hidden bg-white dark:bg-[#071010] border border-gray-100 dark:border-[#111] shadow-2xl">
        <div class="p-6">
          <div class="flex items-start justify-between gap-4">
            <div>
              <h3 class="text-xl font-bold">{{ modalProject.title }}</h3>
              <div class="text-sm text-[#6b6b67] dark:text-[#9f9f9d]">{{ modalProject.type }} • {{ modalProject.year }}</div>
            </div>
            <button @click="closeModal" class="p-2 rounded-md hover:bg-gray-100 dark:hover:bg-white/5" aria-label="Cerrar modal">
              <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none"><path d="M6 6l12 12M6 18L18 6" stroke="currentColor" stroke-width="1.6"/></svg>
            </button>
          </div>

          <div class="mt-4 grid grid-cols-1 md:grid-cols-2 gap-4">
            <div class="aspect-[16/10] rounded-lg bg-gray-100 dark:bg-[#061414] overflow-hidden">
              <img :src="modalProject.image" :alt="modalProject.title" class="w-full h-full object-cover" />
            </div>

            <div>
              <p class="text-sm text-[#4b4b47] dark:text-[#cfcfcf] mb-4">{{ modalProject.description }}</p>

              <div class="mb-3">
                <h4 class="text-xs text-[#6b6b67] dark:text-[#9f9f9d] mb-2">Tecnologías</h4>
                <div class="flex flex-wrap gap-2">
                  <span v-for="t in modalProject.stack" :key="t" class="text-xs px-2 py-1 rounded-md bg-gray-100 dark:bg-white/5">{{ t }}</span>
                </div>
              </div>

              <div class="flex gap-3 mt-4">
                <a v-if="modalProject.demo" :href="modalProject.demo" target="_blank" rel="noopener" class="rounded-md px-4 py-2 bg-[#7c3aed] text-white">Ver demo</a>
                <a href="/contact" class="rounded-md px-4 py-2 border border-gray-200 dark:border-[#111]">Solicitar proyecto</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>
/*
  Welcome.vue — versión avanzada:
  - Theme switch (detecta preferencia y guarda en localStorage).
  - Vista Grid / List, orden, búsqueda, filtros.
  - Modal accesible.
  - Solo depende de Vue 3 + Tailwind (sin Inertia/Router).
*/

import { ref, computed, onMounted, watch, onBeforeUnmount } from 'vue';

/* UI state */
const mobileOpen = ref(false);
const modalOpen = ref(false);
const modalProject = ref({});
const viewMode = ref('grid'); // 'grid' | 'list'
const sortBy = ref('featured'); // 'featured' | 'newest' | 'alpha'
const searchTerm = ref('');
const selectedFilter = ref('Todos');

/* Theme handling */
const theme = ref('auto'); // 'auto' | 'dark' | 'light'
const isDark = ref(false);
const themeClass = computed(() => (isDark.value ? 'dark' : '') );

function applyTheme(pref) {
  if (pref === 'auto') {
    const prefersDark = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches;
    isDark.value = prefersDark;
  } else {
    isDark.value = pref === 'dark';
  }
  // update html class
  if (isDark.value) document.documentElement.classList.add('dark');
  else document.documentElement.classList.remove('dark');
}

function toggleTheme() {
  if (theme.value === 'dark') theme.value = 'light';
  else if (theme.value === 'light') theme.value = 'auto';
  else theme.value = 'dark';
  localStorage.setItem('wp_theme_pref', theme.value);
  applyTheme(theme.value);
}

onMounted(() => {
  const stored = localStorage.getItem('wp_theme_pref');
  theme.value = stored || 'auto';
  applyTheme(theme.value);

  // Listen to system changes if in auto
  if (window.matchMedia) {
    const mq = window.matchMedia('(prefers-color-scheme: dark)');
    mq.addEventListener('change', handleSystemThemeChange);
  }
});

onBeforeUnmount(() => {
  if (window.matchMedia) {
    const mq = window.matchMedia('(prefers-color-scheme: dark)');
    mq.removeEventListener('change', handleSystemThemeChange);
  }
});

function handleSystemThemeChange() {
  if (theme.value === 'auto') applyTheme('auto');
}

/* computed flag for button icons */
watch(isDark, (nv) => {
  // no-op, just reactive
});

/* Projects data (example) */
const projects = ref([
  { id: 'p-1', title: 'Bagisto', type: 'Ecommerce', year: 2024, tags: ['Ecommerce','B2C'], description: 'Tienda modular enterprise con PIM y reglas de precio.', stack: ['Laravel','Vue','Docker'], image: 'https://images.unsplash.com/photo-1522202176988-66273c2fd55f?q=80&w=1400&auto=format&fit=crop&dpr=1', demo: '#' },
  { id: 'p-2', title: 'Krayin', type: 'CRM', year: 2023, tags: ['CRM','SaaS'], description: 'CRM con scoring, pipelines y automatizaciones.', stack: ['Laravel','React','Postgres'], image: 'https://images.unsplash.com/photo-1559523166-9f2a7bb8ce1f?q=80&w=1400&auto=format&fit=crop&dpr=1', demo: '#' },
  { id: 'p-3', title: 'Aureus', type: 'ERP', year: 2022, tags: ['ERP','Accounting'], description: 'ERP para contabilidad, compras y gestión de stock.', stack: ['PHP','Vue','MySQL'], image: 'https://images.unsplash.com/photo-1517694712202-14dd9538aa97?q=80&w=1400&auto=format&fit=crop&dpr=1', demo: '#' },
  { id: 'p-4', title: 'Nova App', type: 'Mobile', year: 2024, tags: ['Mobile','Flutter'], description: 'App multiplataforma en Flutter con onboarding optimizado.', stack: ['Flutter','Firebase'], image: 'https://images.unsplash.com/photo-1519389950473-47ba0277781c?q=80&w=1400&auto=format&fit=crop&dpr=1', demo: '#' },
  { id: 'p-5', title: 'Landing Growth', type: 'Web', year: 2024, tags: ['Landing','CRO'], description: 'Landing A/B con aumento de CVR en +34%.', stack: ['Next.js','Vercel'], image: 'https://images.unsplash.com/photo-1498050108023-c5249f4df085?q=80&w=1400&auto=format&fit=crop&dpr=1', demo: '#' },
  { id: 'p-6', title: 'Retail ERP Sync', type: 'ERP', year: 2023, tags: ['ERP','Retail'], description: 'Sincronización POS ⇄ ERP en tiempo real.', stack: ['Node.js','Postgres'], image: 'https://images.unsplash.com/photo-1518770660439-4636190af475?q=80&w=1400&auto=format&fit=crop&dpr=1', demo: '#' }
]);

const filters = ['Todos', 'Ecommerce', 'CRM', 'ERP', 'Mobile', 'Web'];

const mockupImage = 'https://images.unsplash.com/photo-1522071820081-009f0129c71c?q=80&w=1200&auto=format&fit=crop&dpr=1';
const thumbs = [
  'https://images.unsplash.com/photo-1522202176988-66273c2fd55f?q=80&w=600&auto=format&fit=crop&dpr=1',
  'https://images.unsplash.com/photo-1559523166-9f2a7bb8ce1f?q=80&w=600&auto=format&fit=crop&dpr=1',
  'https://images.unsplash.com/photo-1517694712202-14dd9538aa97?q=80&w=600&auto=format&fit=crop&dpr=1'
];

/* Search + filter + sort */
const filteredProjects = computed(() => {
  const term = searchTerm.value.trim().toLowerCase();
  return projects.value.filter((p) => {
    // filter by selectedFilter
    if (selectedFilter.value !== 'Todos') {
      const sf = selectedFilter.value.toLowerCase();
      const typeMatch = p.type.toLowerCase() === sf;
      const tagMatch = p.tags.some((t) => t.toLowerCase() === sf);
      if (!typeMatch && !tagMatch) return false;
    }
    // search
    if (!term) return true;
    return (
      p.title.toLowerCase().includes(term) ||
      p.description.toLowerCase().includes(term) ||
      p.stack.join(' ').toLowerCase().includes(term) ||
      p.tags.join(' ').toLowerCase().includes(term)
    );
  });
});

const sortedFilteredProjects = computed(() => {
  const copy = [...filteredProjects.value];
  if (sortBy.value === 'newest') {
    copy.sort((a,b) => b.year - a.year);
  } else if (sortBy.value === 'alpha') {
    copy.sort((a,b) => a.title.localeCompare(b.title));
  } else {
    // featured: keep order as is or custom ranking (example: push p-1 first)
    copy.sort((a,b) => (a.id === 'p-1' ? -1 : 0));
  }
  return copy;
});

/* Modal controls */
function openProjectModal(p) {
  modalProject.value = p;
  modalOpen.value = true;
  // lock scroll
  document.documentElement.style.overflow = 'hidden';
}
function closeModal() {
  modalOpen.value = false;
  modalProject.value = {};
  document.documentElement.style.overflow = '';
}

/* Accessibility helper */
function focusProjects() {
  const section = document.getElementById('projects');
  if (section) section.scrollIntoView({ behavior: 'smooth', block: 'start' });
}

/* Testimonials */
const testimonials = [
  { name: 'Laura P.', role: 'Head of Growth', quote: 'Transformaron nuestra adquisición. Estrategia y ejecución impecable.', avatar: 'https://picsum.photos/seed/laura/100' },
  { name: 'Marcos R.', role: 'CEO', quote: 'Subimos 70% las conversiones en 3 meses. Recomendados.', avatar: 'https://picsum.photos/seed/marcos/100' },
  { name: 'Sofia G.', role: 'Product Lead', quote: 'Equipo flexible, entregas rápidas y enfoque en métricas.', avatar: 'https://picsum.photos/seed/sofia/100' }
];

/* Defensive: remove scroll lock on unmount */
onBeforeUnmount(() => {
  document.documentElement.style.overflow = '';
});
</script>

<style scoped>
/* UX & visual polish */
:root { --card-radius: 1rem; }

/* Smooth rounded utilities */
.rounded-3xl { border-radius: var(--card-radius); }

/* Aspect ratio helper used in templates */
.aspect-\[9\/16\] { position: relative; width: 100%; padding-bottom: calc(100% / (9 / 16)); }
.aspect-\[9\/16\] > img, .aspect-\[9\/16\] > * { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; }

/* Prevent text overlap: ensure headings wrap and have space */
h1, h2, h3 { word-break: keep-all; }

/* Small responsive adjustments */
@media (max-width: 640px) {
  h1 { font-size: 1.5rem; }
  .w-64 { width: 12rem; }
}

/* Subtle floating animation for hero decorations (if used) */
@keyframes floaty { 0% { transform: translateY(0px); } 50% { transform: translateY(-8px); } 100% { transform: translateY(0px); } }
.animate-floaty { animation: floaty 6s ease-in-out infinite; }

/* Accessibility focus outlines */
button:focus, a:focus, input:focus, select:focus { outline: 3px solid rgba(124,58,237,0.16); outline-offset: 3px; }

/* Minor shadow */
.shadow-2xl { box-shadow: 0 20px 40px rgba(16,24,40,0.08); }
</style>
