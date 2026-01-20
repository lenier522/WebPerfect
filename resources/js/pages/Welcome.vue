<template>
  <div :class="['min-h-screen font-sans antialiased text-slate-900 dark:text-slate-100 bg-white dark:bg-slate-950', themeClass]" >
    <!-- HEADER -->
    <header class="sticky top-0 z-50 bg-white/80 dark:bg-slate-950/80 backdrop-blur-md border-b border-slate-200 dark:border-slate-800">
      <div class="max-w-7xl mx-auto px-6 lg:px-8 h-16 flex items-center justify-between">
        <a href="/" class="flex items-center gap-3 group" aria-label="Inicio - Perf3ct Solutions">
          <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-indigo-600 to-cyan-500 flex items-center justify-center text-white font-extrabold shadow-lg group-hover:scale-105 transition-transform">
            PS
          </div>
          <div class="leading-tight">
            <div class="text-sm font-bold tracking-tight">Perf3ct Solutions</div>
            <div class="text-[10px] text-slate-500 dark:text-slate-400 font-medium uppercase tracking-wider">Soluciones Digitales</div>
          </div>
        </a>

        <div class="hidden lg:flex items-center gap-8">
          <a href="#about" class="text-sm font-medium hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">Sobre mí</a>
          <a href="#services" class="text-sm font-medium hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">Servicios</a>
          <a href="#portfolio" class="text-sm font-medium hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">Portafolio</a>
          <a href="#testimonials" class="text-sm font-medium hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">Testimonios</a>
        </div>

        <div class="flex items-center gap-4">
          <!-- Theme toggle -->
          <button @click="toggleTheme" :aria-pressed="isDark.toString()" class="p-2 rounded-full text-slate-500 hover:bg-slate-100 dark:hover:bg-slate-800 transition-colors" :title="isDark ? 'Cambiar a tema claro' : 'Cambiar a tema oscuro'">
            <Sun v-if="isDark" class="w-5 h-5" />
            <Moon v-else class="w-5 h-5" />
          </button>

          <a href="#contact" class="hidden sm:inline-flex items-center justify-center rounded-full bg-slate-900 dark:bg-white px-5 py-2 text-sm font-semibold text-white dark:text-slate-900 shadow-sm hover:bg-slate-700 dark:hover:bg-slate-200 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 transition-all">
            Cotizar ahora
          </a>

          <!-- mobile menu button -->
          <button @click="mobileOpen = !mobileOpen" class="lg:hidden p-2 -mr-2 text-slate-600 dark:text-slate-300" aria-label="Menu">
             <Menu v-if="!mobileOpen" class="w-6 h-6" />
             <X v-else class="w-6 h-6" />
          </button>
        </div>
      </div>

      <!-- Mobile Menu -->
      <div v-if="mobileOpen" class="lg:hidden border-t border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-950">
        <nav class="px-6 py-4 flex flex-col gap-4">
          <a href="#about" @click="mobileOpen = false" class="text-sm font-medium py-2 border-b border-slate-100 dark:border-slate-800">Sobre mí</a>
          <a href="#services" @click="mobileOpen = false" class="text-sm font-medium py-2 border-b border-slate-100 dark:border-slate-800">Servicios</a>
          <a href="#portfolio" @click="mobileOpen = false" class="text-sm font-medium py-2 border-b border-slate-100 dark:border-slate-800">Portafolio</a>
          <a href="#testimonials" @click="mobileOpen = false" class="text-sm font-medium py-2 border-b border-slate-100 dark:border-slate-800">Testimonios</a>
          <a href="#contact" @click="mobileOpen = false" class="text-sm font-bold text-indigo-600 dark:text-indigo-400 py-2">Solicitar presupuesto</a>
        </nav>
      </div>
    </header>

    <main>
      <!-- HERO SECTION -->
      <section class="relative pt-20 pb-32 overflow-hidden">
        <!-- Background decoration -->
        <div class="absolute inset-0 -z-10 overflow-hidden">
             <div class="absolute -top-40 -right-40 w-[600px] h-[600px] rounded-full bg-indigo-500/10 blur-[100px]"></div>
             <div class="absolute -bottom-40 -left-40 w-[600px] h-[600px] rounded-full bg-cyan-500/10 blur-[100px]"></div>
        </div>

        <div class="max-w-7xl mx-auto px-6 lg:px-8 flex flex-col lg:flex-row items-center gap-16">
          <div class="lg:w-1/2 space-y-8 text-center lg:text-left">
            <h1 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold tracking-tight text-slate-900 dark:text-white leading-[1.1]">
              Perf3ct Solutions <br/>
              <span class="text-transparent bg-clip-text bg-gradient-to-r from-indigo-600 to-cyan-500">Soluciones digitales</span> que impulsan tu negocio
            </h1>
            <p class="text-lg text-slate-600 dark:text-slate-400 max-w-2xl mx-auto lg:mx-0 leading-relaxed">
              Copywriting, ebooks, logos, música con IA y contenidos profesionales, todo en un solo lugar. Creatividad y estrategia unidas para destacar tu marca.
            </p>
            <div class="flex flex-col sm:flex-row items-center justify-center lg:justify-start gap-4">
              <a href="#contact" class="w-full sm:w-auto inline-flex items-center justify-center gap-2 rounded-full bg-indigo-600 px-8 py-3.5 text-sm font-semibold text-white shadow-lg shadow-indigo-500/30 hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 transition-all hover:scale-105">
                Solicita tu proyecto ahora
                <ArrowRight class="w-4 h-4" />
              </a>
              <a href="#portfolio" class="text-sm font-semibold leading-6 text-slate-900 dark:text-slate-100 hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">
                Ver trabajos <span aria-hidden="true">→</span>
              </a>
            </div>
          </div>

          <!-- Hero Illustration / Mockup -->
          <div class="lg:w-1/2 relative lg:h-[600px] w-full flex items-center justify-center">
             <!-- Abstract Composition using CSS/Icons due to lack of image assets -->
             <div class="relative w-full max-w-md aspect-square">
                 <!-- Floating Elements Animation -->
                 <div class="absolute top-0 right-0 p-6 bg-white dark:bg-slate-800 rounded-2xl shadow-xl flex items-center gap-4 animate-float-slow z-20 border border-slate-100 dark:border-slate-700">
                    <div class="w-12 h-12 rounded-full bg-blue-100 text-blue-600 flex items-center justify-center"><BookOpen class="w-6 h-6" /></div>
                    <div>
                        <div class="text-sm font-bold">Ebooks Premium</div>
                        <div class="text-xs text-slate-500">Diseño & Contenido</div>
                    </div>
                 </div>

                 <div class="absolute bottom-10 left-0 p-6 bg-white dark:bg-slate-800 rounded-2xl shadow-xl flex items-center gap-4 animate-float-medium z-20 border border-slate-100 dark:border-slate-700">
                    <div class="w-12 h-12 rounded-full bg-purple-100 text-purple-600 flex items-center justify-center"><Music class="w-6 h-6" /></div>
                    <div>
                        <div class="text-sm font-bold">Música IA</div>
                        <div class="text-xs text-slate-500">Suno Productions</div>
                    </div>
                </div>

                 <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-80 h-80 bg-gradient-to-tr from-indigo-500 to-cyan-400 rounded-full opacity-20 blur-3xl animate-pulse-slow"></div>
                 
                 <div class="relative z-10 bg-slate-100 dark:bg-slate-800 rounded-3xl overflow-hidden shadow-2xl border border-slate-200 dark:border-slate-700 aspect-[4/5] mx-auto rotate-[-6deg] hover:rotate-0 transition-transform duration-500">
                    <div class="h-full w-full flex flex-col p-6 bg-white dark:bg-slate-900">
                        <div class="w-full h-40 bg-slate-200 dark:bg-slate-800 rounded-lg mb-4 animate-pulse"></div>
                        <div class="w-3/4 h-6 bg-slate-200 dark:bg-slate-800 rounded mb-2"></div>
                        <div class="w-1/2 h-6 bg-slate-200 dark:bg-slate-800 rounded mb-6"></div>
                        <div class="space-y-3">
                            <div class="w-full h-3 bg-slate-100 dark:bg-slate-800 rounded"></div>
                            <div class="w-full h-3 bg-slate-100 dark:bg-slate-800 rounded"></div>
                            <div class="w-5/6 h-3 bg-slate-100 dark:bg-slate-800 rounded"></div>
                        </div>
                    </div>
                 </div>
             </div>
          </div>
        </div>
      </section>

      <!-- ABOUT SECTION -->
      <section id="about" class="py-24 bg-slate-50 dark:bg-slate-900/50">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <div class="flex flex-col md:flex-row items-center gap-12">
                <div class="md:w-1/3 flex justify-center">
                    <div class="relative w-64 h-64">
                         <div class="absolute inset-0 rounded-full border-2 border-indigo-600 border-dashed animate-spin-slow"></div>
                         <div class="absolute inset-2 rounded-full bg-slate-200 dark:bg-slate-800 overflow-hidden flex items-center justify-center shadow-lg">
                            <User class="w-32 h-32 text-slate-400" />
                            <!-- Placeholder for Esequiel's photo -->
                            <!-- <img src="/path/to/profile.jpg" alt="Esequiel Alfaro" class="w-full h-full object-cover" /> -->
                         </div>
                    </div>
                </div>
                <div class="md:w-2/3 text-center md:text-left">
                    <h2 class="text-indigo-600 dark:text-indigo-400 font-semibold tracking-wide uppercase text-sm mb-2">Sobre mí / Nosotros</h2>
                    <h3 class="text-3xl font-bold tracking-tight mb-6">Hola, soy Esequiel Alfaro.</h3>
                    <p class="text-lg text-slate-600 dark:text-slate-300 leading-relaxed mb-8">
                        Soy especialista en soluciones digitales: <strong>copywriting, creación de ebooks, diseño de logos y producción musical con IA</strong>. 
                        Mi misión es ayudarte a que tu negocio o proyecto destaque con contenido profesional, ético y creativo.
                    </p>
                    
                    <div class="grid grid-cols-2 sm:grid-cols-4 gap-6">
                        <div class="flex flex-col items-center gap-2 p-4 bg-white dark:bg-slate-800 rounded-xl shadow-sm hover:shadow-md transition-shadow">
                            <PenTool class="w-8 h-8 text-indigo-500" />
                            <span class="text-sm font-medium">Diseño</span>
                        </div>
                        <div class="flex flex-col items-center gap-2 p-4 bg-white dark:bg-slate-800 rounded-xl shadow-sm hover:shadow-md transition-shadow">
                            <FileText class="w-8 h-8 text-teal-500" />
                            <span class="text-sm font-medium">Copywriting</span>
                        </div>
                         <div class="flex flex-col items-center gap-2 p-4 bg-white dark:bg-slate-800 rounded-xl shadow-sm hover:shadow-md transition-shadow">
                            <BookOpen class="w-8 h-8 text-pink-500" />
                            <span class="text-sm font-medium">Ebooks</span>
                        </div>
                         <div class="flex flex-col items-center gap-2 p-4 bg-white dark:bg-slate-800 rounded-xl shadow-sm hover:shadow-md transition-shadow">
                            <Music class="w-8 h-8 text-purple-500" />
                            <span class="text-sm font-medium">Música IA</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
      </section>

      <!-- SERVICES SECTION -->
      <section id="services" class="py-24 relative overflow-hidden">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
          <div class="text-center mb-16">
            <h2 class="text-indigo-600 dark:text-indigo-400 font-semibold tracking-wide uppercase text-sm mb-2">Mis Servicios</h2>
            <h3 class="text-3xl sm:text-4xl font-bold tracking-tight">Soluciones a tu medida</h3>
            <p class="mt-4 text-slate-600 dark:text-slate-400 max-w-2xl mx-auto">Calidad profesional y precios transparentes para impulsar tu proyecto.</p>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <!-- Service Cards -->
            <div v-for="service in services" :key="service.title" class="group relative bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 rounded-2xl p-8 shadow-sm hover:shadow-xl hover:border-indigo-500/50 transition-all duration-300">
                <div class="absolute top-0 right-0 p-4 opacity-5 group-hover:opacity-10 transition-opacity">
                    <component :is="service.icon" class="w-24 h-24" />
                </div>
                
                <div class="w-12 h-12 rounded-lg bg-indigo-50 dark:bg-slate-800 flex items-center justify-center text-indigo-600 mb-6 group-hover:scale-110 transition-transform bg-gradient-to-br from-indigo-500/10 to-purple-500/10">
                    <component :is="service.icon" class="w-6 h-6" />
                </div>

                <h4 class="text-xl font-bold mb-3 group-hover:text-indigo-600 transition-colors">{{ service.title }}</h4>
                <p class="text-slate-600 dark:text-slate-400 text-sm mb-6 min-h-[60px]">{{ service.description }}</p>

                <div class="flex items-center justify-between border-t border-slate-100 dark:border-slate-800 pt-4 mt-auto">
                    <div class="flex flex-col">
                        <span class="text-xs text-slate-500">Precio estimado</span>
                        <span class="text-lg font-bold text-slate-900 dark:text-white">{{ service.price }}</span>
                    </div>
                </div>
            </div>
          </div>
        </div>
      </section>

     <!-- PORTFOLIO / TRABAJOS DE MUESTRA -->
      <section id="portfolio" class="py-24 bg-slate-50 dark:bg-slate-900/30">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <div class="text-center mb-12">
                 <h2 class="text-indigo-600 dark:text-indigo-400 font-semibold tracking-wide uppercase text-sm mb-2">Portfolio</h2>
                 <h3 class="text-3xl font-bold tracking-tight">Trabajos de muestra</h3>
                 <p class="mt-4 text-slate-600 dark:text-slate-400">Resultados reales que demuestran calidad y compromiso.</p>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Sample Portfolio Item 1 (Ebook) -->
                <div class="group bg-white dark:bg-slate-900 rounded-2xl overflow-hidden shadow-sm hover:shadow-lg transition-all">
                    <div class="aspect-video bg-indigo-100 dark:bg-slate-800 relative flex items-center justify-center overflow-hidden">
                        <BookOpen class="w-16 h-16 text-indigo-300 dark:text-slate-700 group-hover:scale-110 transition-transform" />
                        <!-- <img src="..." class="absolute inset-0 w-full h-full object-cover"> -->
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                             <h4 class="font-bold text-lg">Guía de Marketing Digital</h4>
                             <span class="px-2 py-1 bg-indigo-50 dark:bg-indigo-900/30 text-indigo-700 dark:text-indigo-300 text-xs rounded-full font-medium">Ebook</span>
                        </div>
                        <p class="text-sm text-slate-600 dark:text-slate-400">Diseño completo y redacción de 50 páginas. Aumento de leads en un 20% para el cliente.</p>
                    </div>
                </div>

                 <!-- Sample Portfolio Item 2 (Music) -->
                <div class="group bg-white dark:bg-slate-900 rounded-2xl overflow-hidden shadow-sm hover:shadow-lg transition-all">
                     <div class="aspect-video bg-purple-100 dark:bg-slate-800 relative flex items-center justify-center overflow-hidden">
                        <Music class="w-16 h-16 text-purple-300 dark:text-slate-700 group-hover:scale-110 transition-transform" />
                         <!-- <img src="..." class="absolute inset-0 w-full h-full object-cover"> -->
                         <div class="absolute inset-0 flex items-center justify-center">
                             <div class="w-12 h-12 bg-white/90 rounded-full flex items-center justify-center shadow-lg cursor-pointer hover:scale-105 transition-transform">
                                 <Play class="w-5 h-5 text-purple-600 ml-1" />
                             </div>
                         </div>
                    </div>
                    <div class="p-6">
                         <div class="flex justify-between items-start mb-2">
                             <h4 class="font-bold text-lg">Jingle Corporativo "TechFlow"</h4>
                             <span class="px-2 py-1 bg-purple-50 dark:bg-purple-900/30 text-purple-700 dark:text-purple-300 text-xs rounded-full font-medium">Audio IA</span>
                        </div>
                        <p class="text-sm text-slate-600 dark:text-slate-400">Composición moderna y dinámica generada con Suno para intro de YouTube.</p>
                    </div>
                </div>

                 <!-- Sample Portfolio Item 3 (Web Copy) -->
                <div class="group bg-white dark:bg-slate-900 rounded-2xl overflow-hidden shadow-sm hover:shadow-lg transition-all">
                     <div class="aspect-video bg-teal-100 dark:bg-slate-800 relative flex items-center justify-center overflow-hidden">
                        <Monitor class="w-16 h-16 text-teal-300 dark:text-slate-700 group-hover:scale-110 transition-transform" />
                    </div>
                    <div class="p-6">
                         <div class="flex justify-between items-start mb-2">
                             <h4 class="font-bold text-lg">Landing Page "EcoStore"</h4>
                             <span class="px-2 py-1 bg-teal-50 dark:bg-teal-900/30 text-teal-700 dark:text-teal-300 text-xs rounded-full font-medium">Copywriting</span>
                        </div>
                        <p class="text-sm text-slate-600 dark:text-slate-400">Redacción persuasiva enfocada en conversión. Tono ecológico y cercano.</p>
                    </div>
                </div>
            </div>
            
             <div class="text-center mt-12">
                 <p class="text-sm text-slate-500 italic">"Los trabajos ficticios pueden verse profesionales si demuestran capacidad de entrega."</p>
            </div>
        </div>
      </section>

      <!-- TESTIMONIALS -->
      <section id="testimonials" class="py-24">
         <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <h2 class="text-center text-3xl font-bold mb-16">Lo que dicen mis clientes</h2>
             <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                 <div class="p-8 bg-white dark:bg-slate-900 rounded-2xl border border-slate-100 dark:border-slate-800 shadow-sm relative">
                     <Quote class="w-8 h-8 text-indigo-200 dark:text-slate-700 absolute top-6 left-6" />
                     <p class="mt-6 mb-6 text-slate-600 dark:text-slate-300 italic relative z-10">"El ebook que diseñó Esequiel superó mis expectativas. Muy profesional y entregado a tiempo."</p>
                     <div class="flex items-center gap-3">
                         <div class="w-10 h-10 rounded-full bg-slate-200 flex items-center justify-center text-xs font-bold">MR</div>
                         <div>
                             <div class="font-bold text-sm">María Rodriguez</div>
                             <div class="text-xs text-slate-500">Emprendedora</div>
                         </div>
                     </div>
                 </div>
                 
                  <div class="p-8 bg-white dark:bg-slate-900 rounded-2xl border border-slate-100 dark:border-slate-800 shadow-sm relative">
                     <Quote class="w-8 h-8 text-indigo-200 dark:text-slate-700 absolute top-6 left-6" />
                     <p class="mt-6 mb-6 text-slate-600 dark:text-slate-300 italic relative z-10">"Excelente trabajo con el logo. Captó la esencia de mi marca a la primera. Recomendado."</p>
                     <div class="flex items-center gap-3">
                         <div class="w-10 h-10 rounded-full bg-slate-200 flex items-center justify-center text-xs font-bold">CP</div>
                         <div>
                             <div class="font-bold text-sm">Carlos Pérez</div>
                             <div class="text-xs text-slate-500">CEO Startup</div>
                         </div>
                     </div>
                 </div>
                 
                  <div class="p-8 bg-white dark:bg-slate-900 rounded-2xl border border-slate-100 dark:border-slate-800 shadow-sm relative">
                     <Quote class="w-8 h-8 text-indigo-200 dark:text-slate-700 absolute top-6 left-6" />
                     <p class="mt-6 mb-6 text-slate-600 dark:text-slate-300 italic relative z-10">"La música generada para mi anuncio de Instagram quedó perfecta. Le dio el toque profesional que faltaba."</p>
                     <div class="flex items-center gap-3">
                         <div class="w-10 h-10 rounded-full bg-slate-200 flex items-center justify-center text-xs font-bold">AL</div>
                         <div>
                             <div class="font-bold text-sm">Ana López</div>
                             <div class="text-xs text-slate-500">Marketing Manager</div>
                         </div>
                     </div>
                 </div>
             </div>
         </div>
      </section>

      <!-- CONTACT CTA & FORM -->
        <section id="contact" class="py-24 bg-gradient-to-br from-indigo-900 to-slate-900 text-white relative overflow-hidden">
            <div class="absolute inset-0 bg-[url('https://grainy-gradients.vercel.app/noise.svg')] opacity-20"></div>
            <div class="max-w-7xl mx-auto px-6 lg:px-8 relative z-10">
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
                    <div class="flex flex-col justify-center">
                        <h2 class="text-3xl sm:text-4xl font-bold mb-6">¿Listo para llevar tu proyecto al siguiente nivel?</h2>
                        <p class="text-indigo-200 text-lg mb-8">Contáctame y comencemos hoy mismo. Recibirás una respuesta en menos de 24 horas.</p>
                        
                        <div class="space-y-4">
                            <a href="mailto:contacto@perf3ct.com" class="flex items-center gap-3 text-indigo-100 hover:text-white transition-colors">
                                <Mail class="w-5 h-5" />
                                <span>contacto@perf3ct.com</span>
                            </a>
                            <!-- Socials Placeholder -->
                             <div class="flex gap-4 mt-6">
                                <a href="#" class="p-2 bg-white/10 rounded-full hover:bg-white/20 transition-colors" aria-label="LinkedIn"><Linkedin class="w-5 h-5"/></a>
                                <a href="#" class="p-2 bg-white/10 rounded-full hover:bg-white/20 transition-colors" aria-label="Instagram"><Instagram class="w-5 h-5"/></a>
                                <a href="#" class="p-2 bg-white/10 rounded-full hover:bg-white/20 transition-colors" aria-label="YouTube"><Youtube class="w-5 h-5"/></a>
                            </div>
                        </div>
                    </div>

                    <div class="bg-white text-slate-900 rounded-2xl p-8 shadow-2xl">
                        <h3 class="text-2xl font-bold mb-6">Solicitar presupuesto</h3>
                        <form @submit.prevent="submitForm" class="space-y-4">
                            <div>
                                <label for="name" class="block text-sm font-medium text-slate-700 mb-1">Nombre</label>
                                <input type="text" id="name" v-model="form.name" class="w-full rounded-lg border-slate-200 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 p-2.5 border" placeholder="Tu nombre" required>
                            </div>
                            <div>
                                <label for="email" class="block text-sm font-medium text-slate-700 mb-1">Email</label>
                                <input type="email" id="email" v-model="form.email" class="w-full rounded-lg border-slate-200 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 p-2.5 border" placeholder="tu@email.com" required>
                            </div>
                             <div>
                                <label for="service" class="block text-sm font-medium text-slate-700 mb-1">Servicio de interés</label>
                                <select id="service" v-model="form.service" class="w-full rounded-lg border-slate-200 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 p-2.5 border" required>
                                    <option value="" disabled selected>Selecciona una opción</option>
                                    <option v-for="s in services" :key="s.title" :value="s.title">{{ s.title }}</option>
                                    <option value="Otro">Otro</option>
                                </select>
                            </div>
                            <div>
                                <label for="message" class="block text-sm font-medium text-slate-700 mb-1">Mensaje</label>
                                <textarea id="message" v-model="form.message" rows="3" class="w-full rounded-lg border-slate-200 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 p-2.5 border" placeholder="Cuéntame sobre tu proyecto..." required></textarea>
                            </div>
                            
                            <div class="pt-2">
                                <button type="submit" class="w-full rounded-lg bg-indigo-600 px-5 py-3 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 transition-colors">
                                    Enviar solicitud
                                </button>
                                <p class="text-center text-xs text-slate-500 mt-3 flex items-center justify-center gap-1">
                                    <Lock class="w-3 h-3" /> Pagos seguros vía PayPal / Wise / Cripto
                                </p>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- FOOTER -->
    <footer class="bg-slate-50 dark:bg-slate-950 border-t border-slate-200 dark:border-slate-800 py-12">
        <div class="max-w-7xl mx-auto px-6 lg:px-8 flex flex-col md:flex-row justify-between items-center gap-6">
            <div class="flex items-center gap-3">
                 <div class="w-8 h-8 rounded-lg bg-gradient-to-br from-indigo-600 to-cyan-500 flex items-center justify-center text-white font-bold shadow-md text-xs">PS</div>
                 <span class="text-sm font-semibold text-slate-700 dark:text-slate-300">Perf3ct Solutions</span>
            </div>
            
            <div class="text-sm text-slate-500 dark:text-slate-400">
                © 2026 Perf3ct Solutions – Todos los derechos reservados.
            </div>
            
            <div class="flex gap-6 text-sm">
                <a href="#" class="text-slate-500 hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">Política de Privacidad</a>
                <a href="#" class="text-slate-500 hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors">Términos y Condiciones</a>
            </div>
        </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted, computed, watch } from 'vue';
import { 
  Sun, Moon, Menu, X, ArrowRight, BookOpen, Music, 
  PenTool, FileText, Package, User, Monitor, Play, Quote, Mail,
  Linkedin, Instagram, Youtube, Lock
} from 'lucide-vue-next';

// Mobile menu state
const mobileOpen = ref(false);

// Theme Handling
const isDark = ref(false);
const themeClass = computed(() => isDark.value ? 'dark' : '');

function toggleTheme() {
  isDark.value = !isDark.value;
  localStorage.setItem('ps_theme', isDark.value ? 'dark' : 'light');
  if (isDark.value) document.documentElement.classList.add('dark');
  else document.documentElement.classList.remove('dark');
}

onMounted(() => {
  const stored = localStorage.getItem('ps_theme');
  if (stored) {
    isDark.value = stored === 'dark';
  } else {
    isDark.value = window.matchMedia('(prefers-color-scheme: dark)').matches;
  }
  
  if (isDark.value) document.documentElement.classList.add('dark');
});

// Services Data
const services = [
  { 
    title: 'Copywriting', 
    description: 'Textos persuasivos para tu web, anuncios o campañas que conviertan visitantes en clientes.', 
    price: '$20–$75', 
    icon: FileText 
  },
  { 
    title: 'Investigación / Resúmenes', 
    description: 'Investigaciones y resúmenes profesionales, académicos o corporativos, listos para usar.', 
    price: '$15–$50', 
    icon: BookOpen 
  },
  { 
    title: 'Ebooks', 
    description: 'Ebooks diseñados y escritos profesionalmente, listos para vender o compartir.', 
    price: '$40–$120', 
    icon: BookOpen 
  },
  { 
    title: 'Pack de contenidos', 
    description: 'Combinación de copywriting, investigación y diseño, todo en un solo paquete premium.', 
    price: '$100–$250', 
    icon: Package 
  },
  { 
    title: 'Logos personalizados', 
    description: 'Diseños únicos para tu marca, listos para web, redes y material impreso.', 
    price: '$30–$120', 
    icon: PenTool 
  },
  { 
    title: 'Producción musical IA', 
    description: 'Canciones y jingles personalizados con IA, para publicidad, redes o proyectos musicales.', 
    price: '$60–$180', 
    icon: Music 
  },
];

// Form Handling
const form = ref({
  name: '',
  email: '',
  service: '',
  message: ''
});

function submitForm() {
  alert(`¡Gracias ${form.value.name}! Hemos recibido tu solicitud para "${form.value.service}". Te contactaremos pronto a ${form.value.email}.`);
  // Here you would typically make an inertia visit or axios call
  // form.value = { name: '', email: '', service: '', message: '' };
}

</script>

<style scoped>
/* Keyframes for soft animations */
@keyframes float-slow {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-10px); }
}
@keyframes float-medium {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-6px); }
}
@keyframes spin-slow {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
}

.animate-float-slow {
    animation: float-slow 6s ease-in-out infinite;
}
.animate-float-medium {
    animation: float-medium 5s ease-in-out infinite;
}
.animate-spin-slow {
    animation: spin-slow 12s linear infinite;
}
.animate-pulse-slow {
    animation: pulse 4s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}
</style>
