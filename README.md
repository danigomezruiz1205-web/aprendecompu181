# aprendecompu181<!DOCTYPE html>
<html lang="es" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aprende Informática Básica | Guía de Estudio para Preparatoria</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <!-- FontAwesome para Iconos -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        brand: {
                            50: '#f0f7ff',
                            100: '#e0effe',
                            500: '#2563eb',
                            600: '#1d4ed8',
                            700: '#1e40af',
                            800: '#1e3a8a',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        /* Estilos personalizados adicionales */
        .tab-content {
            display: none;
        }
        .tab-content.active {
            display: block;
        }
        @media print {
            .no-print {
                display: none !important;
            }
            .print-only {
                display: block !important;
            }
            body {
                background: white;
                color: black;
            }
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 font-sans leading-relaxed min-h-screen flex flex-col selection:bg-brand-500 selection:text-white">

    <!-- Barra de lectura superior -->
    <div class="fixed top-0 left-0 w-full h-1.5 bg-slate-200 z-50 no-print">
        <div id="scroll-progress" class="h-full bg-brand-600 transition-all duration-150 w-0"></div>
    </div>

    <!-- Encabezado Principal / Navegación -->
    <header class="sticky top-0 bg-white/95 backdrop-blur-md shadow-sm border-b border-slate-100 z-40 no-print">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <!-- Logo / Título -->
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 bg-brand-600 rounded-xl flex items-center justify-center text-white font-bold text-xl shadow-md shadow-brand-500/20">
                        <i class="fa-solid fa-laptop-code"></i>
                    </div>
                    <div>
                        <span class="text-lg font-bold text-slate-900 block leading-tight">Informática Básica</span>
                        <span class="text-xs text-slate-500 font-medium">Portal de Aprendizaje - Preparatoria</span>
                    </div>
                </div>

                <!-- Menú Navegación Escritorio -->
                <nav class="hidden md:flex space-x-1 lg:space-x-2">
                    <button onclick="switchTab('inicio')" id="nav-inicio" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium transition-colors text-brand-600 bg-brand-50">
                        <i class="fa-solid fa-house mr-1.5"></i>Inicio
                    </button>
                    <button onclick="switchTab('word')" id="nav-word" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-600 hover:bg-slate-100 transition-colors">
                        <i class="fa-solid fa-file-word text-blue-600 mr-1.5"></i>Word / Docs
                    </button>
                    <button onclick="switchTab('powerpoint')" id="nav-powerpoint" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-600 hover:bg-slate-100 transition-colors">
                        <i class="fa-solid fa-file-powerpoint text-orange-600 mr-1.5"></i>PowerPoint
                    </button>
                    <button onclick="switchTab('excel')" id="nav-excel" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-600 hover:bg-slate-100 transition-colors">
                        <i class="fa-solid fa-file-excel text-emerald-600 mr-1.5"></i>Excel / Tablas
                    </button>
                    <button onclick="switchTab('seguridad')" id="nav-seguridad" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-600 hover:bg-slate-100 transition-colors">
                        <i class="fa-solid fa-shield-halved text-teal-600 mr-1.5"></i>Web y Seguridad
                    </button>
                    <button onclick="switchTab('quiz')" id="nav-quiz" class="nav-btn px-3 py-2 rounded-lg text-sm font-medium text-slate-600 hover:text-brand-600 hover:bg-slate-100 transition-colors">
                        <i class="fa-solid fa-pen-to-square text-purple-600 mr-1.5"></i>Evaluación
                    </button>
                </nav>

                <!-- Acciones secundarias -->
                <div class="hidden sm:flex items-center space-x-2">
                    <button onclick="window.print()" class="px-3 py-2 rounded-lg border border-slate-200 text-slate-600 hover:bg-slate-100 text-xs font-semibold flex items-center transition">
                        <i class="fa-solid fa-print mr-1.5"></i> Guardar PDF
                    </button>
                </div>

                <!-- Botón Menú Móvil -->
                <div class="md:hidden flex items-center">
                    <button id="mobile-menu-btn" onclick="toggleMobileMenu()" class="text-slate-600 hover:text-slate-900 p-2 focus:outline-none">
                        <i class="fa-solid fa-bars text-xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Menú Desplegable Móvil -->
        <div id="mobile-menu" class="hidden md:hidden border-t border-slate-200 bg-white px-4 pt-2 pb-4 space-y-1">
            <button onclick="switchTab('inicio'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-700 hover:bg-slate-100 flex items-center">
                <i class="fa-solid fa-house w-6 text-brand-600"></i>Inicio
            </button>
            <button onclick="switchTab('word'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-700 hover:bg-slate-100 flex items-center">
                <i class="fa-solid fa-file-word w-6 text-blue-600"></i>Word / Procesador
            </button>
            <button onclick="switchTab('powerpoint'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-700 hover:bg-slate-100 flex items-center">
                <i class="fa-solid fa-file-powerpoint w-6 text-orange-600"></i>PowerPoint / Slides
            </button>
            <button onclick="switchTab('excel'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-700 hover:bg-slate-100 flex items-center">
                <i class="fa-solid fa-file-excel w-6 text-emerald-600"></i>Excel / Hojas de Cálculo
            </button>
            <button onclick="switchTab('seguridad'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-700 hover:bg-slate-100 flex items-center">
                <i class="fa-solid fa-shield-halved w-6 text-teal-600"></i>Navegación y Seguridad
            </button>
            <button onclick="switchTab('quiz'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-700 hover:bg-slate-100 flex items-center">
                <i class="fa-solid fa-pen-to-square w-6 text-purple-600"></i>Cuestionario Final
            </button>
        </div>
    </header>

    <!-- Contenido Principal -->
    <main class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">

        <!-- ================= MÓDULO 0: INICIO ================= -->
        <section id="tab-inicio" class="tab-content active space-y-8">
            <!-- Hero Banner -->
            <div class="relative bg-gradient-to-r from-brand-800 via-brand-700 to-indigo-900 rounded-3xl p-8 sm:p-12 text-white overflow-hidden shadow-xl">
                <div class="absolute -right-10 -bottom-10 opacity-10 text-white pointer-events-none">
                    <i class="fa-solid fa-desktop text-[280px]"></i>
                </div>
                <div class="relative z-10 max-w-3xl">
                    <span class="inline-block bg-brand-500/30 text-brand-100 text-xs font-semibold tracking-wider uppercase px-3 py-1 rounded-full border border-brand-400/30 mb-4">
                        Programa para Bachillerato General
                    </span>
                    <h1 class="text-3xl sm:text-5xl font-extrabold text-white tracking-tight leading-tight">
                        Domina las Herramientas Digitales Clave
                    </h1>
                    <p class="mt-4 text-base sm:text-lg text-slate-200 leading-relaxed">
                        Bienvenido a la guía práctica de informática básica. Diseñada para darte las competencias fundamentales en redacción académica, diseño de presentaciones, análisis de datos con hojas de cálculo y ciberseguridad.
                    </p>
                    <div class="mt-8 flex flex-wrap gap-4">
                        <button onclick="switchTab('word')" class="px-6 py-3 bg-white text-brand-800 rounded-xl font-bold hover:bg-slate-100 transition shadow-lg flex items-center">
                            Iniciar Primer Módulo <i class="fa-solid fa-arrow-right ml-2"></i>
                        </button>
                        <button onclick="switchTab('quiz')" class="px-6 py-3 bg-brand-600/50 hover:bg-brand-600 text-white border border-brand-400/30 rounded-xl font-medium transition flex items-center">
                            Probar Diagnóstico <i class="fa-solid fa-vial ml-2"></i>
                        </button>
                    </div>
                </div>
            </div>

            <!-- Metodología y Objetivos -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200/80 hover:shadow-md transition">
                    <div class="w-12 h-12 bg-blue-100 text-blue-600 rounded-xl flex items-center justify-center text-xl font-bold mb-4">
                        <i class="fa-solid fa-graduation-cap"></i>
                    </div>
                    <h3 class="text-lg font-bold text-slate-900 mb-2">Enfoque Académico</h3>
                    <p class="text-sm text-slate-600 leading-relaxed">
                        Aprenderás exactamente lo que necesitas para entregar proyectos de calidad escolar: formato APA, resúmenes organizados y gráficos claros.
                    </p>
                </div>

                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200/80 hover:shadow-md transition">
                    <div class="w-12 h-12 bg-emerald-100 text-emerald-600 rounded-xl flex items-center justify-center text-xl font-bold mb-4">
                        <i class="fa-solid fa-keyboard"></i>
                    </div>
                    <h3 class="text-lg font-bold text-slate-900 mb-2">Práctica Interactiva</h3>
                    <p class="text-sm text-slate-600 leading-relaxed">
                        No solo teoría. Cuenta con simuladores donde podrás interactuar con código ficticio de Excel, dar formato en tiempo real y probar diseños.
                    </p>
                </div>

                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200/80 hover:shadow-md transition">
                    <div class="w-12 h-12 bg-purple-100 text-purple-600 rounded-xl flex items-center justify-center text-xl font-bold mb-4">
                        <i class="fa-solid fa-user-shield"></i>
                    </div>
                    <h3 class="text-lg font-bold text-slate-900 mb-2">Cuidado Ciberdigital</h3>
                    <p class="text-sm text-slate-600 leading-relaxed">
                        Protege tu privacidad en redes sociales, identifica amenazas en la web y aprende técnicas avanzadas de búsqueda para tus tareas.
                    </p>
                </div>
            </div>

            <!-- Estructura del curso -->
            <div class="bg-white rounded-2xl p-6 sm:p-8 shadow-sm border border-slate-200/80">
                <h2 class="text-xl font-bold text-slate-900 mb-6 flex items-center">
                    <i class="fa-solid fa-list-check text-brand-600 mr-3"></i> Módulos de Aprendizaje
                </h2>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                    <div onclick="switchTab('word')" class="cursor-pointer p-4 rounded-xl border border-slate-200 hover:border-blue-500 hover:bg-blue-50/50 transition group">
                        <div class="flex items-center space-x-3 mb-2">
                            <i class="fa-solid fa-file-word text-2xl text-blue-600 group-hover:scale-110 transition"></i>
                            <h4 class="font-bold text-slate-800">1. Word / Docs</h4>
                        </div>
                        <p class="text-xs text-slate-500">Formato formal de texto, índices, saltos de página y accesos rápidos.</p>
                    </div>

                    <div onclick="switchTab('powerpoint')" class="cursor-pointer p-4 rounded-xl border border-slate-200 hover:border-orange-500 hover:bg-orange-50/50 transition group">
                        <div class="flex items-center space-x-3 mb-2">
                            <i class="fa-solid fa-file-powerpoint text-2xl text-orange-600 group-hover:scale-110 transition"></i>
                            <h4 class="font-bold text-slate-800">2. PowerPoint</h4>
                        </div>
                        <p class="text-xs text-slate-500">Reglas de diseño visual (6x6), contraste de color e impacto visual.</p>
                    </div>

                    <div onclick="switchTab('excel')" class="cursor-pointer p-4 rounded-xl border border-slate-200 hover:border-emerald-500 hover:bg-emerald-50/50 transition group">
                        <div class="flex items-center space-x-3 mb-2">
                            <i class="fa-solid fa-file-excel text-2xl text-emerald-600 group-hover:scale-110 transition"></i>
                            <h4 class="font-bold text-slate-800">3. Excel / Hojas</h4>
                        </div>
                        <p class="text-xs text-slate-500">Celdas, fórmulas de cálculo básico, promedios y gráficos estadísticos.</p>
                    </div>

                    <div onclick="switchTab('seguridad')" class="cursor-pointer p-4 rounded-xl border border-slate-200 hover:border-teal-500 hover:bg-teal-50/50 transition group">
                        <div class="flex items-center space-x-3 mb-2">
                            <i class="fa-solid fa-shield-halved text-2xl text-teal-600 group-hover:scale-110 transition"></i>
                            <h4 class="font-bold text-slate-800">4. Web y Seguridad</h4>
                        </div>
                        <p class="text-xs text-slate-500">Búsqueda avanzada, detección de Phishing y comportamiento ético.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= MÓDULO 1: WORD / PROCESADOR DE TEXTO ================= -->
        <section id="tab-word" class="tab-content space-y-8">
            <div class="bg-blue-600 text-white rounded-2xl p-6 sm:p-8 shadow-md">
                <div class="flex items-center space-x-3 mb-2">
                    <i class="fa-solid fa-file-word text-3xl"></i>
                    <span class="text-sm font-semibold uppercase tracking-wider text-blue-200">Módulo 1</span>
                </div>
                <h2 class="text-2xl sm:text-3xl font-extrabold">Procesador de Textos (Word / Google Docs)</h2>
                <p class="mt-2 text-blue-100 max-w-3xl">
                    Aprende a maquetar reportes, ensayos y trabajos escolares con presentación profesional siguiendo los lineamientos académicos necesarios.
                </p>
            </div>

            <!-- Contenido Téorico / Guía -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <div class="lg:col-span-2 space-y-6">
                    <!-- Formato Estándar APA -->
                    <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                        <h3 class="text-lg font-bold text-slate-900 mb-4 flex items-center text-blue-600">
                            <i class="fa-solid fa-align-left mr-2"></i> Formato Académico Estándar
                        </h3>
                        <p class="text-sm text-slate-600 mb-4">
                            Para que un trabajo de preparatoria luzca formal, es crucial seguir pautas de edición uniformes. Estas son las más utilizadas en instituciones educativas:
                        </p>
                        <ul class="space-y-3 text-sm text-slate-700">
                            <li class="flex items-start">
                                <i class="fa-solid fa-circle-check text-blue-500 mt-1 mr-2 text-xs"></i>
                                <span><strong>Tipografía recomendada:</strong> Fuentes legibles como <em>Arial</em>, <em>Calibri</em> (11 pts) o <em>Times New Roman</em> (12 pts).</span>
                            </li>
                            <li class="flex items-start">
                                <i class="fa-solid fa-circle-check text-blue-500 mt-1 mr-2 text-xs"></i>
                                <span><strong>Interlineado y Alineación:</strong> Usa interlineado de 1.5 líneas para facilitar la lectura. El texto principal debe estar <strong>justificado</strong> o alineado a la izquierda según el profesor.</span>
                            </li>
                            <li class="flex items-start">
                                <i class="fa-solid fa-circle-check text-blue-500 mt-1 mr-2 text-xs"></i>
                                <span><strong>Márgenes:</strong> Conserva los márgenes estándar (2.5 cm superior e inferior, 3 cm lateral) para evitar cortes en la impresión.</span>
                            </li>
                        </ul>
                    </div>

                    <!-- Estructura e Índices -->
                    <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                        <h3 class="text-lg font-bold text-slate-900 mb-4 flex items-center text-blue-600">
                            <i class="fa-solid fa-list-ol mr-2"></i> Índices Automáticos y Encabezados
                        </h3>
                        <p class="text-sm text-slate-600 mb-3">
                            Olvídate de hacer tablas de contenido manualmente escribiendo puntos hasta el número de página. Usa la herramienta nativa:
                        </p>
                        <ol class="list-decimal list-inside text-sm text-slate-700 space-y-2">
                            <li>Aplica los estilos de texto <strong>Título 1</strong>, <strong>Título 2</strong> o <strong>Subtítulo</strong> a tus encabezados.</li>
                            <li>Ve a la pestaña <em>Referencias</em> en la barra de menú superior.</li>
                            <li>Haz clic en <strong>Tabla de contenido</strong> y elige un formato. Se actualizará automáticamente si agregas más páginas.</li>
                        </ol>
                    </div>
                </div>

                <!-- Atajos de teclado clave -->
                <div class="space-y-6">
                    <div class="bg-slate-900 text-white p-6 rounded-2xl shadow-md">
                        <h3 class="text-md font-bold mb-4 text-blue-400 flex items-center">
                            <i class="fa-solid fa-bolt mr-2"></i> Atajos Imprescindibles (Teclado)
                        </h3>
                        <div class="space-y-3 text-xs">
                            <div class="flex justify-between items-center border-b border-slate-800 pb-2">
                                <span class="text-slate-300">Copiar texto</span>
                                <kbd class="bg-slate-800 text-blue-300 px-2 py-1 rounded font-mono border border-slate-700">Ctrl + C</kbd>
                            </div>
                            <div class="flex justify-between items-center border-b border-slate-800 pb-2">
                                <span class="text-slate-300">Pegar texto</span>
                                <kbd class="bg-slate-800 text-blue-300 px-2 py-1 rounded font-mono border border-slate-700">Ctrl + V</kbd>
                            </div>
                            <div class="flex justify-between items-center border-b border-slate-800 pb-2">
                                <span class="text-slate-300">Deshacer cambio</span>
                                <kbd class="bg-slate-800 text-blue-300 px-2 py-1 rounded font-mono border border-slate-700">Ctrl + Z</kbd>
                            </div>
                            <div class="flex justify-between items-center border-b border-slate-800 pb-2">
                                <span class="text-slate-300">Seleccionar todo</span>
                                <kbd class="bg-slate-800 text-blue-300 px-2 py-1 rounded font-mono border border-slate-700">Ctrl + E</kbd>
                            </div>
                            <div class="flex justify-between items-center border-b border-slate-800 pb-2">
                                <span class="text-slate-300">Buscar palabra</span>
                                <kbd class="bg-slate-800 text-blue-300 px-2 py-1 rounded font-mono border border-slate-700">Ctrl + B</kbd>
                            </div>
                            <div class="flex justify-between items-center">
                                <span class="text-slate-300">Salto de página</span>
                                <kbd class="bg-slate-800 text-blue-300 px-2 py-1 rounded font-mono border border-slate-700">Ctrl + Enter</kbd>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- SIMULADOR INTERACTIVO: WORD -->
            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 overflow-hidden no-print">
                <div class="bg-slate-100 px-6 py-4 border-b border-slate-200 flex justify-between items-center">
                    <h3 class="font-bold text-slate-800 flex items-center">
                        <i class="fa-solid fa-terminal text-blue-600 mr-2"></i> Práctica Interactiva: Mini Editor de Texto
                    </h3>
                    <span class="text-xs bg-blue-100 text-blue-800 font-semibold px-2.5 py-0.5 rounded">Ejercicio en vivo</span>
                </div>
                <div class="p-6">
                    <!-- Barra de herramientas simulada -->
                    <div class="flex flex-wrap gap-2 p-2 bg-slate-50 border border-slate-200 rounded-xl mb-4">
                        <button onclick="formatDoc('bold')" class="p-2 bg-white hover:bg-slate-200 border rounded text-slate-700 font-bold w-9 h-9" title="Negrita">N</button>
                        <button onclick="formatDoc('italic')" class="p-2 bg-white hover:bg-slate-200 border rounded text-slate-700 italic w-9 h-9" title="Cursiva">K</button>
                        <button onclick="formatDoc('underline')" class="p-2 bg-white hover:bg-slate-200 border rounded text-slate-700 underline w-9 h-9" title="Subrayado">S</button>
                        <div class="h-6 w-px bg-slate-300 my-auto mx-1"></div>
                        <button onclick="formatDoc('justifyLeft')" class="p-2 bg-white hover:bg-slate-200 border rounded text-slate-700 w-9 h-9" title="Izquierda"><i class="fa-solid fa-align-left"></i></button>
                        <button onclick="formatDoc('justifyCenter')" class="p-2 bg-white hover:bg-slate-200 border rounded text-slate-700 w-9 h-9" title="Centro"><i class="fa-solid fa-align-center"></i></button>
                        <button onclick="formatDoc('justifyRight')" class="p-2 bg-white hover:bg-slate-200 border rounded text-slate-700 w-9 h-9" title="Derecha"><i class="fa-solid fa-align-right"></i></button>
                        <div class="h-6 w-px bg-slate-300 my-auto mx-1"></div>
                        <button onclick="formatDoc('insertUnorderedList')" class="p-2 bg-white hover:bg-slate-200 border rounded text-slate-700 w-9 h-9" title="Viñetas"><i class="fa-solid fa-list-ul"></i></button>
                    </div>

                    <!-- Hoja simulada -->
                    <div id="editor-word" contenteditable="true" class="min-h-[160px] p-6 bg-white border border-slate-300 rounded-xl shadow-inner focus:outline-none focus:ring-2 focus:ring-blue-500 text-slate-800 text-sm">
                        <b>Instrucciones:</b> Selecciona este texto con tu ratón y utiliza los botones de la barra superior para dar formato. Puedes cambiar la alineación, aplicar negritas o agregar viñetas para practicar tus habilidades antes de entregar una tarea real.
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= MÓDULO 2: POWERPOINT / PRESENTACIONES ================= -->
        <section id="tab-powerpoint" class="tab-content space-y-8">
            <div class="bg-orange-600 text-white rounded-2xl p-6 sm:p-8 shadow-md">
                <div class="flex items-center space-x-3 mb-2">
                    <i class="fa-solid fa-file-powerpoint text-3xl"></i>
                    <span class="text-sm font-semibold uppercase tracking-wider text-orange-200">Módulo 2</span>
                </div>
                <h2 class="text-2xl sm:text-3xl font-extrabold">Presentaciones Digitales Efectivas</h2>
                <p class="mt-2 text-orange-100 max-w-3xl">
                    Las diapositivas son un soporte visual para tus exposiciones verbales, no un libro de texto traducido a pantallas. Aprende a causar impacto visual.
                </p>
            </div>

            <!-- Principios de Diseño -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <!-- Regla 6x6 -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                    <div class="w-10 h-10 bg-orange-100 text-orange-600 rounded-lg flex items-center justify-center font-bold text-lg mb-3">
                        6×6
                    </div>
                    <h3 class="text-lg font-bold text-slate-900 mb-2">La Regla de Oro del 6×6</h3>
                    <p class="text-sm text-slate-600 leading-relaxed">
                        Para evitar saturar a tu audiencia, procura incluir un máximo de <strong>6 líneas de texto por diapositiva</strong> y un promedio de <strong>6 palabras por línea</strong>. Prioriza viñetas breves e ideas clave.
                    </p>
                </div>

                <!-- Contraste y Tipografía -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                    <div class="w-10 h-10 bg-orange-100 text-orange-600 rounded-lg flex items-center justify-center font-bold text-lg mb-3">
                        <i class="fa-solid fa-palette"></i>
                    </div>
                    <h3 class="text-lg font-bold text-slate-900 mb-2">Contraste y Visibilidad</h3>
                    <p class="text-sm text-slate-600 leading-relaxed">
                        Asegúrate de que haya un alto contraste entre el fondo y la letra. Utiliza texto oscuro sobre fondos claros (o viceversa). Evita fondos con patrones complejos que dificulten la lectura a distancia.
                    </p>
                </div>
            </div>

            <!-- SIMULADOR INTERACTIVO: POWERPOINT -->
            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6 no-print">
                <h3 class="font-bold text-slate-800 mb-4 flex items-center">
                    <i class="fa-solid fa-sliders text-orange-600 mr-2"></i> Simulador de Diapositiva: Buenas vs Malas Prácticas
                </h3>
                
                <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                    <!-- Controles -->
                    <div class="bg-slate-50 p-4 rounded-xl border border-slate-200 space-y-4 text-xs">
                        <div>
                            <label class="font-bold text-slate-700 block mb-1">Tema / Fondo:</label>
                            <select id="ppt-theme" onchange="updateSlideSim()" class="w-full p-2 bg-white border border-slate-300 rounded-lg">
                                <option value="clean">Limpio / Profesional (Recomendado)</option>
                                <option value="dark">Modo Oscuro Elegante</option>
                                <option value="bad">Malo: Fondo saturado y poco contraste</option>
                            </select>
                        </div>

                        <div>
                            <label class="font-bold text-slate-700 block mb-1">Carga de Texto:</label>
                            <select id="ppt-text" onchange="updateSlideSim()" class="w-full p-2 bg-white border border-slate-300 rounded-lg">
                                <option value="good">Puntos Clave / Síntesis (Regla 6x6)</option>
                                <option value="bad">Párrafo Infinito (Saturado)</option>
                            </select>
                        </div>

                        <div>
                            <label class="font-bold text-slate-700 block mb-1">Uso de Imágenes:</label>
                            <select id="ppt-image" onchange="updateSlideSim()" class="w-full p-2 bg-white border border-slate-300 rounded-lg">
                                <option value="yes">Imagen ilustrativa relevante</option>
                                <option value="no">Sin imágenes</option>
                            </select>
                        </div>
                    </div>

                    <!-- Vista Previa Diapositiva -->
                    <div class="lg:col-span-2">
                        <div id="slide-preview" class="aspect-video w-full rounded-xl p-6 shadow-md transition-all flex flex-col justify-between border relative overflow-hidden bg-white text-slate-900 border-slate-300">
                            <!-- Contenido dinámico renderizado con JS -->
                        </div>
                        <p id="slide-feedback" class="mt-2 text-xs font-semibold text-slate-600 text-center"></p>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= MÓDULO 3: EXCEL / HOJAS DE CÁLCULO ================= -->
        <section id="tab-excel" class="tab-content space-y-8">
            <div class="bg-emerald-600 text-white rounded-2xl p-6 sm:p-8 shadow-md">
                <div class="flex items-center space-x-3 mb-2">
                    <i class="fa-solid fa-file-excel text-3xl"></i>
                    <span class="text-sm font-semibold uppercase tracking-wider text-emerald-200">Módulo 3</span>
                </div>
                <h2 class="text-2xl sm:text-3xl font-extrabold">Hojas de Cálculo (Excel / Sheets)</h2>
                <p class="mt-2 text-emerald-100 max-w-3xl">
                    Las hojas de cálculo son herramientas matemáticas automatizadas para organizar datos, realizar cálculos numéricos instantáneos y generar representaciones gráficas.
                </p>
            </div>

            <!-- Conceptos Básicos -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <div class="bg-white p-5 rounded-xl border border-slate-200">
                    <span class="text-xs font-bold text-emerald-600 uppercase">Concepto 1</span>
                    <h4 class="font-bold text-slate-900 mt-1">Filas y Columnas</h4>
                    <p class="text-xs text-slate-600 mt-2">Las <strong>columnas</strong> están identificadas con letras (A, B, C...) y las <strong>filas</strong> con números (1, 2, 3...). La intersección es una <strong>Celda</strong> (Ej. A1).</p>
                </div>

                <div class="bg-white p-5 rounded-xl border border-slate-200">
                    <span class="text-xs font-bold text-emerald-600 uppercase">Concepto 2</span>
                    <h4 class="font-bold text-slate-900 mt-1">El Signo Igual (=)</h4>
                    <p class="text-xs text-slate-600 mt-2">Toda fórmula o función en Excel <strong>debe comenzar obligatoriamente con el signo igual (=)</strong>. De lo contrario, Excel lo tratará como texto simple.</p>
                </div>

                <div class="bg-white p-5 rounded-xl border border-slate-200">
                    <span class="text-xs font-bold text-emerald-600 uppercase">Concepto 3</span>
                    <h4 class="font-bold text-slate-900 mt-1">Rangos (:)</h4>
                    <p class="text-xs text-slate-600 mt-2">Un bloque continuo de celdas se expresa con dos puntos. Por ejemplo, <code>A1:A5</code> contempla las celdas A1, A2, A3, A4 y A5.</p>
                </div>
            </div>

            <!-- Tabla de Fórmulas -->
            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 overflow-hidden">
                <div class="p-6 border-b border-slate-100">
                    <h3 class="font-bold text-slate-900">Fórmulas Esenciales que Debes Dominar</h3>
                </div>
                <div class="overflow-x-auto">
                    <table class="w-full text-left border-collapse text-xs sm:text-sm">
                        <thead>
                            <tr class="bg-slate-50 text-slate-700 border-b border-slate-200">
                                <th class="p-3 font-semibold">Función</th>
                                <th class="p-3 font-semibold">Sintaxis</th>
                                <th class="p-3 font-semibold">Explicación del Funcionamiento</th>
                            </tr>
                        </thead>
                        <tbody class="divide-y divide-slate-100 text-slate-600">
                            <tr>
                                <td class="p-3 font-bold text-emerald-700">SUMA</td>
                                <td class="p-3 font-mono text-slate-800 bg-slate-50 rounded">=SUMA(A1:A10)</td>
                                <td class="p-3">Suma todos los valores numéricos dentro del rango seleccionado.</td>
                            </tr>
                            <tr>
                                <td class="p-3 font-bold text-emerald-700">PROMEDIO</td>
                                <td class="p-3 font-mono text-slate-800 bg-slate-50 rounded">=PROMEDIO(B1:B5)</td>
                                <td class="p-3">Calcula la media aritmética (suma total dividida entre el número de elementos).</td>
                            </tr>
                            <tr>
                                <td class="p-3 font-bold text-emerald-700">CONTAR</td>
                                <td class="p-3 font-mono text-slate-800 bg-slate-50 rounded">=CONTAR(C1:C20)</td>
                                <td class="p-3">Cuenta cuántas celdas contienen números dentro de un conjunto de datos.</td>
                            </tr>
                            <tr>
                                <td class="p-3 font-bold text-emerald-700">SI (Condicional)</td>
                                <td class="p-3 font-mono text-slate-800 bg-slate-50 rounded">=SI(A1>=6, "Aprobado", "Reprobado")</td>
                                <td class="p-3">Evalúa una condición lógica y devuelve un valor si es verdadera y otro si es falsa.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- SIMULADOR INTERACTIVO: EXCEL -->
            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6 no-print">
                <h3 class="font-bold text-slate-800 mb-2 flex items-center">
                    <i class="fa-solid fa-calculator text-emerald-600 mr-2"></i> Simulador de Hoja de Cálculo
                </h3>
                <p class="text-xs text-slate-500 mb-4">Introduce calificaciones en las celdas A1, A2 y A3, luego prueba una fórmula para ver el resultado simulado en vivo.</p>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <!-- Tabla simulada -->
                    <div class="border border-slate-300 rounded-lg overflow-hidden bg-slate-50">
                        <table class="w-full text-center border-collapse text-xs">
                            <thead>
                                <tr class="bg-slate-200 text-slate-700">
                                    <th class="p-2 border border-slate-300 w-12"></th>
                                    <th class="p-2 border border-slate-300 font-bold">A (Calificaciones)</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td class="bg-slate-200 font-bold p-2 border border-slate-300">1</td>
                                    <td class="p-1 border border-slate-300 bg-white">
                                        <input id="cell-a1" type="number" value="8" oninput="calculateExcel()" class="w-full text-center p-1 focus:outline-none">
                                    </td>
                                </tr>
                                <tr>
                                    <td class="bg-slate-200 font-bold p-2 border border-slate-300">2</td>
                                    <td class="p-1 border border-slate-300 bg-white">
                                        <input id="cell-a2" type="number" value="9" oninput="calculateExcel()" class="w-full text-center p-1 focus:outline-none">
                                    </td>
                                </tr>
                                <tr>
                                    <td class="bg-slate-200 font-bold p-2 border border-slate-300">3</td>
                                    <td class="p-1 border border-slate-300 bg-white">
                                        <input id="cell-a3" type="number" value="7" oninput="calculateExcel()" class="w-full text-center p-1 focus:outline-none">
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>

                    <!-- Panel de Entrada de Fórmula -->
                    <div class="space-y-3 bg-emerald-50/50 p-4 rounded-xl border border-emerald-100 flex flex-col justify-center">
                        <label class="text-xs font-bold text-slate-700">Escribe o selecciona una fórmula:</label>
                        <div class="flex gap-2">
                            <span class="p-2 bg-slate-200 rounded font-mono font-bold text-slate-700 text-sm">=</span>
                            <input id="excel-formula" type="text" value="PROMEDIO(A1:A3)" class="w-full p-2 border border-slate-300 rounded text-xs font-mono uppercase focus:ring-2 focus:ring-emerald-500 focus:outline-none">
                            <button onclick="calculateExcel()" class="px-4 py-2 bg-emerald-600 text-white rounded font-bold text-xs hover:bg-emerald-700">Ejecutar</button>
                        </div>
                        <div class="flex flex-wrap gap-1 text-[10px]">
                            <button onclick="setFormula('SUMA(A1:A3)')" class="px-2 py-1 bg-white border border-slate-300 rounded hover:bg-slate-100">PROBAR: SUMA(A1:A3)</button>
                            <button onclick="setFormula('PROMEDIO(A1:A3)')" class="px-2 py-1 bg-white border border-slate-300 rounded hover:bg-slate-100">PROBAR: PROMEDIO(A1:A3)</button>
                        </div>
                        <div class="mt-2 p-3 bg-white rounded border border-emerald-200 text-xs">
                            <span class="text-slate-500 block">Resultado en Celda de Salida:</span>
                            <span id="excel-result" class="text-xl font-bold text-emerald-700">8</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= MÓDULO 4: NAVEGACIÓN Y CIBERSEGURIDAD ================= -->
        <section id="tab-seguridad" class="tab-content space-y-8">
            <div class="bg-teal-600 text-white rounded-2xl p-6 sm:p-8 shadow-md">
                <div class="flex items-center space-x-3 mb-2">
                    <i class="fa-solid fa-shield-halved text-3xl"></i>
                    <span class="text-sm font-semibold uppercase tracking-wider text-teal-200">Módulo 4</span>
                </div>
                <h2 class="text-2xl sm:text-3xl font-extrabold">Navegación Web y Ciberseguridad</h2>
                <p class="mt-2 text-teal-100 max-w-3xl">
                    Internet es una fuente infinita de conocimiento, pero requiere criterio analítico para investigar fuentes confiables y precaución para proteger tus datos personales.
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <!-- Búsqueda Avanzada -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                    <h3 class="text-lg font-bold text-slate-900 mb-3 flex items-center text-teal-600">
                        <i class="fa-solid fa-magnifying-glass mr-2"></i> Operadores de Búsqueda Avanzada
                    </h3>
                    <p class="text-xs text-slate-600 mb-4">Usa estos trucos en los buscadores para obtener resultados exactos para tus tareas:</p>
                    <div class="space-y-3 text-xs">
                        <div class="p-2.5 bg-slate-50 rounded-lg border border-slate-200">
                            <code class="font-bold text-teal-700">"frase exacta"</code>
                            <p class="text-slate-600 mt-1">Busca las palabras juntas en ese orden exacto. Ejemplo: <code>"Revolución Mexicana"</code></p>
                        </div>
                        <div class="p-2.5 bg-slate-50 rounded-lg border border-slate-200">
                            <code class="font-bold text-teal-700">filetype:pdf</code>
                            <p class="text-slate-600 mt-1">Filtra solo archivos en formato PDF (ideal para libros académicos). Ejemplo: <code>Física Newton filetype:pdf</code></p>
                        </div>
                        <div class="p-2.5 bg-slate-50 rounded-lg border border-slate-200">
                            <code class="font-bold text-teal-700">site:.edu</code>
                            <p class="text-slate-600 mt-1">Limita la búsqueda a páginas web de universidades e instituciones educativas.</p>
                        </div>
                    </div>
                </div>

                <!-- Ciberseguridad y Phishing -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                    <h3 class="text-lg font-bold text-slate-900 mb-3 flex items-center text-teal-600">
                        <i class="fa-solid fa-user-lock mr-2"></i> Identificación de Amenazas (Phishing)
                    </h3>
                    <p class="text-xs text-slate-600 mb-4">El Phishing es la técnica con la que cibercriminales intentan engañarte para robar contraseñas o datos bancarios.</p>
                    <ul class="space-y-2 text-xs text-slate-700">
                        <li class="flex items-start">
                            <i class="fa-solid fa-triangle-exclamation text-amber-500 mr-2 mt-0.5"></i>
                            <span><strong>Desconfía de la urgencia:</strong> Mensajes del tipo "Tu cuenta se cerrará en 1 hora si no ingresas aquí".</span>
                        </li>
                        <li class="flex items-start">
                            <i class="fa-solid fa-triangle-exclamation text-amber-500 mr-2 mt-0.5"></i>
                            <span><strong>Verifica el dominio/URL:</strong> Un correo oficial de Google no vendrá de <code>soporte-google123@gmail-free.com</code>.</span>
                        </li>
                        <li class="flex items-start">
                            <i class="fa-solid fa-triangle-exclamation text-amber-500 mr-2 mt-0.5"></i>
                            <span><strong>Verificación en dos pasos (2FA):</strong> Actívala siempre en tus redes sociales y correo institucional.</span>
                        </li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- ================= MÓDULO 5: EVALUACIÓN / QUIZ ================= -->
        <section id="tab-quiz" class="tab-content space-y-8">
            <div class="bg-purple-700 text-white rounded-2xl p-6 sm:p-8 shadow-md">
                <div class="flex items-center space-x-3 mb-2">
                    <i class="fa-solid fa-pen-to-square text-3xl"></i>
                    <span class="text-sm font-semibold uppercase tracking-wider text-purple-200">Módulo Final</span>
                </div>
                <h2 class="text-2xl sm:text-3xl font-extrabold">Evaluación de Diagnóstico y Aprendizaje</h2>
                <p class="mt-2 text-purple-100 max-w-3xl">
                    Pon a prueba los conocimientos adquiridos en este portal. Responde las 5 preguntas y obtén tu retroalimentación inmediata.
                </p>
            </div>

            <!-- Cuestionario Interactivo -->
            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6 sm:p-8 max-w-3xl mx-auto no-print">
                <form id="quiz-form" onsubmit="evaluateQuiz(event)" class="space-y-6">
                    
                    <!-- Pregunta 1 -->
                    <div class="space-y-2">
                        <p class="font-bold text-slate-800 text-sm sm:text-base">1. ¿Con qué símbolo debe comenzar obligatoriamente cualquier fórmula en Excel?</p>
                        <div class="space-y-1.5 text-xs sm:text-sm">
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q1" value="a" required> <span>Símbolo de gato o numeral (#)</span>
                            </label>
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q1" value="b"> <span>Signo de igual (=)</span>
                            </label>
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q1" value="c"> <span>Signo de pesos ($)</span>
                            </label>
                        </div>
                    </div>

                    <!-- Pregunta 2 -->
                    <div class="space-y-2">
                        <p class="font-bold text-slate-800 text-sm sm:text-base">2. ¿En qué consiste la regla del 6x6 para presentaciones en PowerPoint?</p>
                        <div class="space-y-1.5 text-xs sm:text-sm">
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q2" value="a" required> <span>Máximo 6 diapositivas por exposición de 6 minutos.</span>
                            </label>
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q2" value="b"> <span>Máximo 6 líneas de texto por diapositiva y unas 6 palabras por línea.</span>
                            </label>
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q2" value="c"> <span>Usar 6 colores y 6 tipos de letra por trabajo.</span>
                            </label>
                        </div>
                    </div>

                    <!-- Pregunta 3 -->
                    <div class="space-y-2">
                        <p class="font-bold text-slate-800 text-sm sm:text-base">3. ¿Qué atajo de teclado se utiliza para deshacer la última acción realizada?</p>
                        <div class="space-y-1.5 text-xs sm:text-sm">
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q3" value="a" required> <span>Ctrl + Z</span>
                            </label>
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q3" value="b"> <span>Ctrl + C</span>
                            </label>
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q3" value="c"> <span>Ctrl + X</span>
                            </label>
                        </div>
                    </div>

                    <!-- Pregunta 4 -->
                    <div class="space-y-2">
                        <p class="font-bold text-slate-800 text-sm sm:text-base">4. Para buscar un archivo en formato PDF específicamente en Google, ¿qué operador usas?</p>
                        <div class="space-y-1.5 text-xs sm:text-sm">
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q4" value="a" required> <span>search:pdf</span>
                            </label>
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q4" value="b"> <span>filetype:pdf</span>
                            </label>
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q4" value="c"> <span>format.pdf</span>
                            </label>
                        </div>
                    </div>

                    <!-- Pregunta 5 -->
                    <div class="space-y-2">
                        <p class="font-bold text-slate-800 text-sm sm:text-base">5. ¿Cuál es una señal clara de un ataque de Phishing?</p>
                        <div class="space-y-1.5 text-xs sm:text-sm">
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q5" value="a" required> <span>Un correo con urgencia extrema y enlace sospechoso pidiendo tu contraseña.</span>
                            </label>
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q5" value="b"> <span>Un mensaje oficial de tu escuela enviado desde el dominio institucional.</span>
                            </label>
                            <label class="flex items-center space-x-2 p-2 rounded hover:bg-slate-50 border cursor-pointer">
                                <input type="radio" name="q5" value="c"> <span>Una actualización de software descargada del sitio oficial del fabricante.</span>
                            </label>
                        </div>
                    </div>

                    <div class="pt-4 border-t border-slate-200 flex justify-end">
                        <button type="submit" class="px-6 py-3 bg-purple-600 hover:bg-purple-700 text-white rounded-xl font-bold transition shadow-md">
                            Calcular Mi Puntaje
                        </button>
                    </div>
                </form>

                <!-- Resultado del Quiz -->
                <div id="quiz-result" class="hidden mt-6 p-6 rounded-xl border text-center space-y-3">
                    <div id="quiz-score-badge" class="text-3xl font-extrabold"></div>
                    <p id="quiz-feedback" class="text-sm text-slate-700"></p>
                    <button onclick="resetQuiz()" class="text-xs text-purple-600 underline font-semibold mt-2">Intentar de nuevo</button>
                </div>
            </div>
        </section>

    </main>

    <!-- Pie de página -->
    <footer class="bg-slate-900 text-slate-400 py-8 border-t border-slate-800 mt-12 no-print">
        <div class="max-w-7xl mx-auto px-4 text-center text-xs space-y-2">
            <p class="font-semibold text-slate-300">Portal Educativo de Informática Básica - Nivel Bachillerato</p>
            <p>Recurso Didáctico para Estudiantes y Docentes. Diseñado con fines académicos.</p>
        </div>
    </footer>

    <!-- LÓGICA JAVASCRIPT NATIVA -->
    <script>
        // 1. Control de Navegación por Pestañas
        function switchTab(tabId) {
            // Ocultar todos los contenidos
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.remove('active');
            });

            // Desmarcar todos los botones de navegación
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('text-brand-600', 'bg-brand-50');
                btn.classList.add('text-slate-600');
            });

            // Mostrar el módulo actual
            const targetTab = document.getElementById('tab-' + tabId);
            if(targetTab) {
                targetTab.classList.add('active');
            }

            // Destacar el botón activo
            const activeBtn = document.getElementById('nav-' + tabId);
            if(activeBtn) {
                activeBtn.classList.add('text-brand-600', 'bg-brand-50');
                activeBtn.classList.remove('text-slate-600');
            }

            // Scroll suave hacia arriba
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Menu móvil
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
        }

        // 2. Barra de Progreso de Lectura
        window.addEventListener('scroll', () => {
            const winScroll = document.documentElement.scrollTop || document.body.scrollTop;
            const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrolled = (winScroll / height) * 100;
            document.getElementById('scroll-progress').style.width = scrolled + '%';
        });

        // 3. Mini Editor de Texto (Simulador Word)
        function formatDoc(cmd, value = null) {
            document.execCommand(cmd, false, value);
        }

        // 4. Simulador Diapositivas PowerPoint
        function updateSlideSim() {
            const theme = document.getElementById('ppt-theme').value;
            const textStyle = document.getElementById('ppt-text').value;
            const hasImage = document.getElementById('ppt-image').value;
            const preview = document.getElementById('slide-preview');
            const feedback = document.getElementById('slide-feedback');

            // Resetear estilos
            preview.className = "aspect-video w-full rounded-xl p-6 shadow-md transition-all flex flex-col justify-between border relative overflow-hidden ";

            if (theme === 'clean') {
                preview.className += "bg-white text-slate-900 border-slate-300";
            } else if (theme === 'dark') {
                preview.className += "bg-slate-900 text-white border-slate-700";
            } else {
                preview.className += "bg-yellow-300 text-yellow-100 border-yellow-400"; // Mal contraste
            }

            let textHTML = "";
            if (textStyle === 'good') {
                textHTML = `
                    <h4 class="font-bold text-lg sm:text-xl">El Ciclo del Agua</h4>
                    <ul class="list-disc list-inside text-xs sm:text-sm space-y-1 mt-2">
                        <li>Evaporación por calor solar.</li>
                        <li>Condensación en nubes.</li>
                        <li>Precipitación en forma de lluvia.</li>
                    </ul>
                `;
            } else {
                textHTML = `
                    <h4 class="font-bold text-sm">El Ciclo del Agua</h4>
                    <p class="text-[10px] sm:text-xs leading-tight mt-1">
                        El ciclo del agua es el proceso de circulación del agua entre las distintas partes de la hidrosfera. Se trata de un ciclo biogeoquímico en el que hay una intervención mínima de reacciones químicas, porque el agua casi no experimenta transformación estructural y solo cambia de estado físico a través de la evaporación y la condensación continuas en la atmósfera...
                    </p>
                `;
            }

            let imgHTML = "";
            if (hasImage === 'yes') {
                imgHTML = `
                    <div class="mt-2 w-full h-24 bg-slate-200/50 rounded-lg flex items-center justify-center text-xs font-semibold">
                        <i class="fa-solid fa-image mr-2 text-slate-400"></i> [ Esquema Ilustrativo del Ciclo ]
                    </div>
                `;
            }

            preview.innerHTML = `<div>${textHTML}</div>${imgHTML}`;

            // Retroalimentación pedagógica
            if (theme === 'bad') {
                feedback.innerHTML = "⚠️ <span class='text-red-600'>¡Cuidado! El texto amarillo sobre fondo amarillo claro es ilegible.</span>";
            } else if (textStyle === 'bad') {
                feedback.innerHTML = "⚠️ <span class='text-amber-600'>Demasiado texto saturado. Tu audiencia se distraerá leyendo en lugar de escucharte.</span>";
            } else {
                feedback.innerHTML = "✅ <span class='text-emerald-600'>¡Excelente diseño! Contraste alto, puntos clave y soporte visual limpio.</span>";
            }
        }

        // Inicializar vista diapositiva
        updateSlideSim();

        // 5. Simulador Hoja de Cálculo Excel
        function setFormula(f) {
            document.getElementById('excel-formula').value = f;
            calculateExcel();
        }

        function calculateExcel() {
            const v1 = parseFloat(document.getElementById('cell-a1').value) || 0;
            const v2 = parseFloat(document.getElementById('cell-a2').value) || 0;
            const v3 = parseFloat(document.getElementById('cell-a3').value) || 0;
            const formula = document.getElementById('excel-formula').value.toUpperCase().trim();
            const resultElem = document.getElementById('excel-result');

            if (formula.includes("SUMA")) {
                resultElem.innerText = (v1 + v2 + v3);
            } else if (formula.includes("PROMEDIO")) {
                const avg = (v1 + v2 + v3) / 3;
                resultElem.innerText = avg.toFixed(1);
            } else {
                resultElem.innerText = "Fórmula no reconocida";
            }
        }

        // 6. Evaluación / Quiz
        function evaluateQuiz(e) {
            e.preventDefault();
            const answers = { q1: 'b', q2: 'b', q3: 'a', q4: 'b', q5: 'a' };
            let score = 0;
            
            const formData = new FormData(document.getElementById('quiz-form'));
            for (let [key, val] of formData.entries()) {
                if (answers[key] === val) {
                    score++;
                }
            }

            const resultBox = document.getElementById('quiz-result');
            const scoreBadge = document.getElementById('quiz-score-badge');
            const feedback = document.getElementById('quiz-feedback');

            resultBox.classList.remove('hidden');
            scoreBadge.innerText = `${score} / 5 Aciertos`;

            if (score === 5) {
                resultBox.className = "mt-6 p-6 rounded-xl border border-emerald-200 bg-emerald-50 text-center space-y-2";
                scoreBadge.className = "text-3xl font-extrabold text-emerald-700";
                feedback.innerText = "¡Felicidades! Has demostrado un dominio completo de los conceptos informáticos fundamentales.";
            } else if (score >= 3) {
                resultBox.className = "mt-6 p-6 rounded-xl border border-amber-200 bg-amber-50 text-center space-y-2";
                scoreBadge.className = "text-3xl font-extrabold text-amber-700";
                feedback.innerText = "¡Buen trabajo! Has aprobado el test, pero te recomendamos repasar los módulos donde tuviste dudas.";
            } else {
                resultBox.className = "mt-6 p-6 rounded-xl border border-red-200 bg-red-50 text-center space-y-2";
                scoreBadge.className = "text-3xl font-extrabold text-red-700";
                feedback.innerText = "Te recomendamos revisar con atención el material didáctico de cada módulo e intentarlo nuevamente.";
            }
        }

        function resetQuiz() {
            document.getElementById('quiz-form').reset();
            document.getElementById('quiz-result').classList.add('hidden');
        }
    </script>
</body>
</html>
