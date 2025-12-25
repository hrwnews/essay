<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hope Rising World | Essay & Voice Expression Competition</title>
    
    <!-- Fonts: Noto Sans for UI, Merriweather for Reading Texts, Noto Sans SC/JP/KR for Asian scripts -->
    <link href="https://fonts.googleapis.com/css2?family=Merriweather:ital,wght@0,300;0,400;0,700;1,400&family=Noto+Sans:wght@300;400;600;700&family=Noto+Sans+SC:wght@400;700&family=Noto+Sans+JP:wght@400;700&family=Noto+Sans+KR:wght@400;700&display=swap" rel="stylesheet">
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        hrw: {
                            blue: '#1e3a8a', // Dark Blue
                            gold: '#fbbf24', // Warm Gold
                            light: '#f3f4f6',
                            text: '#1f2937'
                        }
                    },
                    fontFamily: {
                        sans: ['Noto Sans', 'Noto Sans SC', 'Noto Sans JP', 'Noto Sans KR', 'sans-serif'],
                        serif: ['Merriweather', 'serif'],
                    }
                }
            }
        }
    </script>
    <style>
        .step-active { @apply border-hrw-blue text-hrw-blue font-bold; }
        .step-inactive { @apply border-gray-300 text-gray-400; }
        .step-completed { @apply border-green-500 text-green-600; }
        
        /* Smooth fade for view switching */
        .view-section {
            animation: fadeIn 0.3s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body class="bg-gray-50 text-hrw-text font-sans flex flex-col min-h-screen">

    <!-- Navigation -->
    <nav class="bg-white shadow-sm sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex items-center cursor-pointer" onclick="switchView('home')">
                    <div class="bg-hrw-blue text-white p-2 rounded-lg mr-2">
                        <i data-lucide="globe-2"></i>
                    </div>
                    <span class="font-bold text-xl tracking-tight text-hrw-blue hidden sm:block">Hope Rising World</span>
                    <span class="font-bold text-xl tracking-tight text-hrw-blue sm:hidden">HRW</span>
                </div>
                
                <div class="hidden md:flex items-center space-x-6">
                    <a href="#" onclick="switchView('home')" class="text-gray-600 hover:text-hrw-blue transition font-medium" data-i18n="nav_home">Home</a>
                    <a href="#" onclick="switchView('competition')" class="text-gray-600 hover:text-hrw-blue transition font-medium" data-i18n="nav_competition">Competition</a>
                    <a href="#" onclick="switchView('guidelines')" class="text-gray-600 hover:text-hrw-blue transition font-medium" data-i18n="nav_guidelines">Guidelines</a>
                    <button onclick="switchView('judge')" class="text-sm font-semibold text-gray-400 hover:text-hrw-blue uppercase tracking-wider" data-i18n="nav_judge">Judge Portal</button>
                </div>

                <div class="flex items-center gap-3">
                    <!-- Language Selector -->
                    <div class="relative group">
                        <select id="language-select" onchange="changeLanguage(this.value)" class="bg-gray-50 border border-gray-300 text-gray-700 text-sm rounded-lg focus:ring-hrw-blue focus:border-hrw-blue block w-full p-2 appearance-none pr-8 cursor-pointer hover:bg-gray-100 transition">
                            <option value="en">🇺🇸 English</option>
                            <option value="es">🇪🇸 Español</option>
                            <option value="fr">🇫🇷 Français</option>
                            <option value="de">🇩🇪 Deutsch</option>
                            <option value="ko">🇰🇷 한국어</option>
                            <option value="ja">🇯🇵 日本語</option>
                            <option value="hi">🇮🇳 हिन्दी</option>
                            <option value="pt">🇧🇷 Português</option>
                            <option value="zh">🇨🇳 中文</option>
                        </select>
                        <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700">
                            <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
                        </div>
                    </div>

                    <button onclick="switchView('submission')" class="bg-hrw-blue text-white px-4 py-2 rounded-full font-semibold hover:bg-blue-800 transition shadow-lg transform hover:-translate-y-0.5 text-sm whitespace-nowrap" data-i18n="nav_submit">
                        Start Submission
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Main Content Area -->
    <main id="app-content" class="flex-grow">
        <!-- Content injected via JS -->
    </main>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white mt-12">
        <div class="max-w-7xl mx-auto px-4 py-12 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div>
                    <h3 class="text-lg font-bold text-hrw-gold mb-4">Hope Rising World</h3>
                    <p class="text-gray-400 text-sm" data-i18n="footer_desc">Empowering youth through authentic expression in the age of AI.</p>
                </div>
                <div>
                    <h3 class="text-lg font-bold mb-4" data-i18n="footer_resources">Resources</h3>
                    <ul class="space-y-2 text-gray-400 text-sm">
                        <li><a href="#" onclick="switchView('guidelines')" class="hover:text-white" data-i18n="nav_guidelines">Participant Guide</a></li>
                        <li><a href="#" onclick="switchView('guidelines')" class="hover:text-white" data-i18n="rubric_title">Scoring Rubric</a></li>
                        <li><a href="#" onclick="switchView('guidelines')" class="hover:text-white" data-i18n="integrity_title">Integrity Policy</a></li>
                    </ul>
                </div>
                <div>
                    <h3 class="text-lg font-bold mb-4" data-i18n="footer_contact">Contact</h3>
                    <p class="text-gray-400 text-sm">info@hoperisingworld.org</p>
                </div>
            </div>
            <div class="border-t border-gray-800 mt-8 pt-8 text-center text-gray-500 text-sm">
                &copy; 2026 Hope Rising World. All rights reserved.
            </div>
        </div>
    </footer>

    <!-- Templates for Views -->
    
    <!-- 1. HOME VIEW (Option C + Main Theme) -->
    <template id="view-home">
        <div class="view-section">
            <!-- Hero with Main Theme Statement -->
            <div class="relative bg-hrw-blue text-white overflow-hidden">
                <div class="absolute inset-0 opacity-10">
                     <!-- Abstract pattern placeholder -->
                     <svg width="100%" height="100%"><pattern id="pattern" width="40" height="40" patternUnits="userSpaceOnUse"><circle cx="2" cy="2" r="1" fill="#fff"></circle></pattern><rect width="100%" height="100%" fill="url(#pattern)"></rect></svg>
                </div>
                <div class="max-w-7xl mx-auto px-4 py-24 sm:px-6 lg:px-8 relative z-10 text-center">
                    <span class="bg-hrw-gold text-blue-900 text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wide mb-4 inline-block" data-i18n="hero_badge">Global Competition 2026</span>
                    <h1 class="text-4xl md:text-6xl font-bold mb-6 tracking-tight leading-tight" data-i18n="hero_title">
                        Authentic Voice in the Age of AI
                    </h1>
                    <p class="text-xl md:text-2xl text-blue-100 max-w-4xl mx-auto mb-10 font-light leading-relaxed" data-i18n="hero_subtitle">
                        In a world where technology can imitate writing, HRW celebrates what cannot be automated: human understanding, personal perspective, and sincere expression—in both writing and voice.
                    </p>
                    <div class="flex flex-col sm:flex-row justify-center gap-4">
                        <button onclick="switchView('submission')" class="bg-hrw-gold text-blue-900 px-8 py-4 rounded-lg font-bold text-lg hover:bg-yellow-400 transition shadow-xl" data-i18n="cta_start">
                            Start Your Submission
                        </button>
                        <button onclick="switchView('guidelines')" class="border border-white text-white px-8 py-4 rounded-lg font-semibold hover:bg-white hover:text-hrw-blue transition" data-i18n="cta_guide">
                            Download Guide
                        </button>
                    </div>
                </div>
            </div>

            <!-- Option C: Longer Proposal Introduction -->
            <div class="max-w-4xl mx-auto px-4 py-20 sm:px-6 lg:px-8">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-gray-900 mb-6" data-i18n="about_title">About the Competition</h2>
                </div>
                <!-- UPDATED: Replaced hardcoded English with data-i18n target for full text injection -->
                <div class="prose prose-lg text-gray-600 mx-auto" data-i18n="about_body">
                    <!-- Default English content loaded via JS or initial state -->
                    <p class="mb-6">Hope Rising World (HRW) is launching a new global educational competition...</p>
                </div>
            </div>
        </div>
    </template>

    <!-- 4. COMPETITION VIEW (Option B Short Intro) -->
    <template id="view-competition">
        <div class="view-section">
            <div class="bg-hrw-blue text-white py-16">
                <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
                    <h1 class="text-4xl font-bold mb-6" data-i18n="page_comp_title">The Competition</h1>
                    <div class="text-xl text-blue-100 leading-relaxed" data-i18n="page_comp_desc">
                        <!-- Option B text injected here -->
                    </div>
                </div>
            </div>

            <div class="max-w-7xl mx-auto px-4 py-16 sm:px-6 lg:px-8">
                <!-- Who Can Participate -->
                <div class="mb-20">
                    <h2 class="text-3xl font-bold text-gray-900 mb-8 text-center" data-i18n="who_can_participate">Who Can Participate</h2>
                    <div class="grid md:grid-cols-3 gap-6">
                        <div class="bg-white p-6 rounded-xl border border-gray-200 shadow-sm text-center">
                            <div class="w-16 h-16 bg-blue-50 text-blue-600 rounded-full flex items-center justify-center mx-auto mb-4 font-bold text-2xl">E</div>
                            <h3 class="text-xl font-bold mb-2">Elementary</h3>
                            <p class="text-gray-500">Grades 4-5</p>
                        </div>
                        <div class="bg-white p-6 rounded-xl border border-blue-200 shadow-md ring-2 ring-blue-50 text-center transform scale-105">
                            <div class="w-16 h-16 bg-hrw-blue text-white rounded-full flex items-center justify-center mx-auto mb-4 font-bold text-2xl">M</div>
                            <h3 class="text-xl font-bold mb-2">Middle School</h3>
                            <p class="text-gray-500">Grades 6-8</p>
                        </div>
                        <div class="bg-white p-6 rounded-xl border border-gray-200 shadow-sm text-center">
                            <div class="w-16 h-16 bg-blue-50 text-blue-600 rounded-full flex items-center justify-center mx-auto mb-4 font-bold text-2xl">H</div>
                            <h3 class="text-xl font-bold mb-2">High School</h3>
                            <p class="text-gray-500">Grades 9-12</p>
                        </div>
                    </div>
                </div>

                <!-- Timeline -->
                <div class="bg-gray-900 text-white rounded-2xl p-8 md:p-12">
                    <h2 class="text-2xl font-bold mb-8 text-center" data-i18n="timeline_title">Competition Timeline</h2>
                    <div class="flex flex-col md:flex-row justify-between items-center gap-8 relative">
                        <div class="hidden md:block absolute top-1/2 left-0 w-full h-1 bg-gray-700 -z-0"></div>
                        <div class="relative z-10 text-center bg-gray-900 px-4">
                            <div class="w-4 h-4 bg-hrw-gold rounded-full mx-auto mb-4"></div>
                            <h4 class="font-bold text-lg" data-i18n="time_open">Submissions Open</h4>
                            <p class="text-gray-400 text-sm">March 1, 2026</p>
                        </div>
                        <div class="relative z-10 text-center bg-gray-900 px-4">
                            <div class="w-4 h-4 bg-gray-600 rounded-full mx-auto mb-4"></div>
                            <h4 class="font-bold text-lg" data-i18n="time_deadline">Deadline</h4>
                            <p class="text-gray-400 text-sm">May 15, 2026</p>
                        </div>
                        <div class="relative z-10 text-center bg-gray-900 px-4">
                            <div class="w-4 h-4 bg-gray-600 rounded-full mx-auto mb-4"></div>
                            <h4 class="font-bold text-lg" data-i18n="time_finalists">Finalists Announced</h4>
                            <p class="text-gray-400 text-sm">June 30, 2026</p>
                        </div>
                        <div class="relative z-10 text-center bg-gray-900 px-4">
                            <div class="w-4 h-4 bg-gray-600 rounded-full mx-auto mb-4"></div>
                            <h4 class="font-bold text-lg" data-i18n="time_gala">Awards Gala</h4>
                            <p class="text-gray-400 text-sm">August 2026</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </template>

    <!-- 5. GUIDELINES VIEW (Option A Intro) -->
    <template id="view-guidelines">
        <div class="view-section">
            <div class="bg-white border-b border-gray-200 py-16">
                <div class="max-w-4xl mx-auto px-4 text-center">
                    <h1 class="text-3xl font-bold text-gray-900 mb-6" data-i18n="page_guide_title">Official Guidelines</h1>
                    <div class="prose prose-lg text-gray-600 mx-auto" data-i18n="guide_body">
                        <!-- Option A text injected here -->
                    </div>
                </div>
            </div>

            <div class="max-w-4xl mx-auto px-4 py-12 grid gap-12">
                <div class="bg-red-50 border border-red-100 rounded-xl p-8">
                    <h2 class="text-xl font-bold text-red-800 mb-4 flex items-center gap-2">
                        <i data-lucide="shield-alert"></i> <span data-i18n="integrity_title">Integrity & AI Policy</span>
                    </h2>
                    <div class="space-y-4 text-red-900">
                        <p data-i18n="integrity_desc">Strict Prohibition: The use of AI tools to write your essay or generate your voice is strictly prohibited.</p>
                    </div>
                </div>

                <div>
                     <h2 class="text-xl font-bold text-gray-900 mb-4" data-i18n="rubric_header">How You Are Scored</h2>
                     <div class="overflow-hidden border border-gray-200 rounded-lg">
                         <table class="min-w-full divide-y divide-gray-200">
                             <tbody class="bg-white divide-y divide-gray-200">
                                 <tr>
                                     <td class="px-6 py-4 whitespace-nowrap font-bold" data-i18n="comp_1_title">Written Essay</td>
                                     <td class="px-6 py-4 whitespace-nowrap text-blue-600 font-bold">40%</td>
                                 </tr>
                                 <tr>
                                     <td class="px-6 py-4 whitespace-nowrap font-bold" data-i18n="comp_2_title">Audio Reading</td>
                                     <td class="px-6 py-4 whitespace-nowrap text-blue-600 font-bold">30%</td>
                                 </tr>
                                 <tr>
                                     <td class="px-6 py-4 whitespace-nowrap font-bold" data-i18n="comp_3_title">Oral Response</td>
                                     <td class="px-6 py-4 whitespace-nowrap text-blue-600 font-bold">30%</td>
                                 </tr>
                             </tbody>
                         </table>
                     </div>
                </div>
            </div>
        </div>
    </template>

    <!-- 2. SUBMISSION PORTAL VIEW -->
    <template id="view-submission">
        <div class="max-w-4xl mx-auto px-4 py-12 view-section">
            <div class="mb-8">
                <h1 class="text-3xl font-bold text-gray-900">Competition Submission</h1>
                <p class="text-gray-600">Participant: <span class="font-semibold text-gray-900">Student ID: #82910</span></p>
            </div>
            <!-- Simple placeholder steps for submission logic -->
             <div class="bg-white p-8 rounded-xl shadow-lg border border-gray-200 min-h-[400px] flex items-center justify-center text-center">
                <div>
                    <h2 class="text-xl font-bold mb-4">Submission Portal</h2>
                    <p class="text-gray-500">Please switch to "English" for full submission functionality in this demo.</p>
                    <button onclick="switchView('home')" class="mt-4 text-hrw-blue hover:underline">Return Home</button>
                </div>
            </div>
        </div>
    </template>

    <!-- 3. JUDGE PORTAL VIEW -->
    <template id="view-judge">
        <div class="max-w-7xl mx-auto px-4 py-8 view-section">
             <div class="bg-white p-8 rounded-xl shadow-lg border border-gray-200 min-h-[400px] flex items-center justify-center text-center">
                <div>
                    <h2 class="text-xl font-bold mb-4">Judge Portal</h2>
                    <p class="text-gray-500">Authorized Personnel Only.</p>
                    <button onclick="switchView('home')" class="mt-4 text-hrw-blue hover:underline">Return Home</button>
                </div>
            </div>
        </div>
    </template>

    <script>
        // --- TRANSLATION DATA ---
        const translations = {
            en: {
                nav_home: "Home", nav_competition: "Competition", nav_guidelines: "Guidelines", nav_judge: "Judge Portal", nav_submit: "Start Submission",
                hero_badge: "Global Competition 2026",
                hero_title: "Authentic Voice in the Age of AI",
                hero_subtitle: "In a world where technology can imitate writing, HRW celebrates what cannot be automated: human understanding, personal perspective, and sincere expression—in both writing and voice.",
                cta_start: "Start Your Submission", cta_guide: "Download Guide",
                about_title: "About the Competition",
                // Option C (Home)
                about_body: `
                    <p class="mb-6">Hope Rising World (HRW) is launching a new global educational competition: the <strong>Essay & Voice Expression Competition</strong>—a program designed to protect and elevate what matters most in young people’s learning: meaning, integrity, and authentic voice.</p>
                    <p class="mb-6">Traditional essay competitions often reward surface-level polish and technical fluency. In today’s world, those signals are increasingly unreliable. AI writing tools can generate sophisticated essays in seconds, making it harder to identify genuine authorship and even harder to encourage students to build the essential human skills of comprehension, reflection, and expression.</p>
                    <p class="mb-6">HRW’s competition introduces an integrated model that evaluates both written and spoken expression to highlight real understanding. This structure supports fairness and strengthens integrity by allowing judges to evaluate consistency between text and voice. It also creates an encouraging environment for students: accent or non-native fluency is not penalized if meaning is clear; what matters is sincerity, clarity, and personal interpretation.</p>
                    <div class="bg-blue-50 p-8 rounded-xl text-center mt-10"><p class="text-xl font-bold text-hrw-blue italic mb-2">"Your thoughts matter. Your voice matters. Your honesty matters."</p></div>`,
                comp_1_title: "1. Written Essay", comp_2_title: "2. Audio Reading", comp_3_title: "3. Spontaneous Oral Response",
                page_comp_title: "The Competition",
                // Option B (Competition)
                page_comp_desc: "The HRW Essay & Voice Expression Competition is built for the AI era. Instead of rewarding memorized or polished writing, we recognize authentic understanding and personal expression. Students submit an original essay plus two short voice recordings: an essay reading and a spontaneous response. Together, these reveal real comprehension, ownership, and clarity—because your voice matters more than perfect writing.",
                who_can_participate: "Who Can Participate",
                timeline_title: "Competition Timeline",
                time_open: "Submissions Open", time_deadline: "Deadline", time_finalists: "Finalists Announced", time_gala: "Awards Gala",
                page_guide_title: "Official Guidelines",
                // Option A (Guidelines)
                guide_body: `
                    <p class="mb-4">Hope Rising World (HRW) proposes the Essay & Voice Expression Competition, a future-ready global program designed for the age of artificial intelligence. While AI can generate polished essays instantly, it cannot replace a young person’s authentic thinking, lived perspective, and human voice. This competition shifts the focus from “perfect writing” to real comprehension and personal expression.</p>
                    <p class="mb-4">Participants complete three connected tasks: (1) write an original essay based on a provided reading, (2) record an audio reading of their essay, and (3) submit a short spontaneous oral response. Evaluating both writing and voice allows HRW to honor sincerity, strengthen integrity, and measure genuine understanding in a fair, age-appropriate way.</p>
                    <p class="mb-4">The HRW competition is open to youth worldwide and welcomes native and non-native English speakers. Our guiding message is simple:</p>
                    <p class="font-bold text-hrw-blue text-xl italic">“Do not aim for perfection. Aim for honesty.”</p>`,
                integrity_title: "Integrity & AI Policy",
                integrity_desc: "Strict Prohibition: The use of AI tools to write your essay or generate your voice is strictly prohibited.",
                rubric_header: "How You Are Scored",
                rubric_title: "Scoring Rubric",
                footer_desc: "Empowering youth through authentic expression in the age of AI.",
                footer_resources: "Resources", footer_contact: "Contact"
            },
            es: {
                nav_home: "Inicio", nav_competition: "Competencia", nav_guidelines: "Pautas", nav_judge: "Portal de Juez", nav_submit: "Iniciar Envío",
                hero_badge: "Competencia Global 2026",
                hero_title: "Voz Auténtica en la Era de la IA",
                hero_subtitle: "En un mundo donde la tecnología puede imitar la escritura, HRW celebra lo que no se puede automatizar: la comprensión humana, la perspectiva personal y la expresión sincera.",
                cta_start: "Comenzar Envío", cta_guide: "Descargar Guía",
                about_title: "Sobre la Competencia",
                about_body: `
                    <p class="mb-6">Hope Rising World (HRW) lanza una nueva competencia educativa global: la <strong>Competencia de Ensayo y Expresión de Voz</strong>, un programa diseñado para proteger y elevar lo que más importa en el aprendizaje de los jóvenes: significado, integridad y voz auténtica.</p>
                    <p class="mb-6">Las competencias de ensayo tradicionales a menudo recompensan la fluidez técnica superficial. En el mundo de hoy, esas señales son cada vez menos confiables. Las herramientas de escritura de IA pueden generar ensayos sofisticados en segundos, lo que dificulta identificar la autoría genuina y alentar a los estudiantes a desarrollar habilidades humanas esenciales.</p>
                    <p class="mb-6">La competencia de HRW presenta un modelo integrado que evalúa tanto la expresión escrita como la oral para resaltar la comprensión real. Esta estructura apoya la equidad y fortalece la integridad, permitiendo a los jueces evaluar la coherencia entre el texto y la voz. También crea un ambiente alentador: no se penaliza el acento si el significado es claro; lo que importa es la sinceridad, la claridad y la interpretación personal.</p>
                    <div class="bg-blue-50 p-8 rounded-xl text-center mt-10"><p class="text-xl font-bold text-hrw-blue italic mb-2">"Tus pensamientos importan. Tu voz importa. Tu honestidad importa."</p></div>`,
                comp_1_title: "1. Ensayo Escrito", comp_2_title: "2. Lectura de Audio", comp_3_title: "3. Respuesta Oral",
                page_comp_title: "La Competencia",
                page_comp_desc: "La Competencia de Ensayo y Expresión de Voz de HRW está diseñada para la era de la IA. En lugar de recompensar la escritura memorizada o pulida, reconocemos la comprensión auténtica y la expresión personal. Los estudiantes envían un ensayo original más dos grabaciones de voz cortas: una lectura del ensayo y una respuesta espontánea. Juntos, estos revelan comprensión real, propiedad y claridad, porque tu voz importa más que la escritura perfecta.",
                who_can_participate: "Quién Puede Participar",
                timeline_title: "Cronograma",
                time_open: "Apertura", time_deadline: "Fecha Límite", time_finalists: "Finalistas", time_gala: "Gala de Premios",
                page_guide_title: "Pautas Oficiales",
                guide_body: `
                    <p class="mb-4">Hope Rising World (HRW) propone la Competencia de Ensayo y Expresión de Voz, un programa global preparado para el futuro y diseñado para la era de la inteligencia artificial. Si bien la IA puede generar ensayos pulidos al instante, no puede reemplazar el pensamiento auténtico, la perspectiva vivida y la voz humana de un joven.</p>
                    <p class="mb-4">Los participantes completan tres tareas conectadas: (1) escribir un ensayo original basado en una lectura proporcionada, (2) grabar una lectura de audio de su ensayo, y (3) enviar una respuesta oral espontánea corta. Evaluar tanto la escritura como la voz permite a HRW honrar la sinceridad y medir la comprensión genuina de una manera justa.</p>
                    <p class="mb-4">La competencia HRW está abierta a jóvenes de todo el mundo y da la bienvenida a hablantes nativos y no nativos de inglés. Nuestro mensaje guía es simple:</p>
                    <p class="font-bold text-hrw-blue text-xl italic">“No busques la perfección. Busca la honestidad.”</p>`,
                integrity_title: "Política de Integridad",
                integrity_desc: "Prohibición estricta: El uso de herramientas de IA para escribir su ensayo está estrictamente prohibido.",
                rubric_header: "Cómo se Califica", rubric_title: "Rúbrica de Puntuación",
                footer_desc: "Empoderando a la juventud a través de la expresión auténtica.",
                footer_resources: "Recursos", footer_contact: "Contacto"
            },
            fr: {
                nav_home: "Accueil", nav_competition: "Compétition", nav_guidelines: "Directives", nav_judge: "Portail Juges", nav_submit: "Commencer",
                hero_badge: "Compétition Mondiale 2026",
                hero_title: "Voix Authentique à l'Ère de l'IA",
                hero_subtitle: "Dans un monde où la technologie peut imiter l'écriture, HRW célèbre ce qui ne peut être automatisé : la compréhension humaine et l'expression sincère.",
                cta_start: "Commencer", cta_guide: "Télécharger le Guide",
                about_title: "À Propos",
                about_body: `
                    <p class="mb-6">Hope Rising World (HRW) lance une nouvelle compétition éducative mondiale : la <strong>Compétition d'Essai et d'Expression Vocale</strong> — un programme conçu pour protéger et élever ce qui compte le plus dans l'apprentissage des jeunes : le sens, l'intégrité et la voix authentique.</p>
                    <p class="mb-6">Les concours d'essais traditionnels récompensent souvent le polissage superficiel et la fluidité technique. Dans le monde d'aujourd'hui, ces signaux sont de moins en moins fiables. Les outils d'écriture IA peuvent générer des essais sophistiqués en quelques secondes, ce qui rend plus difficile l'identification de l'auteur véritable et encore plus difficile d'encourager les étudiants à développer des compétences humaines essentielles.</p>
                    <p class="mb-6">La compétition de HRW introduit un modèle intégré qui évalue à la fois l'expression écrite et orale pour mettre en évidence la compréhension réelle. Cette structure soutient l'équité et renforce l'intégrité en permettant aux juges d'évaluer la cohérence entre le texte et la voix. Elle crée également un environnement encourageant : l'accent ou la fluidité non native n'est pas pénalisé si le sens est clair ; ce qui compte, c'est la sincérité, la clarté et l'interprétation personnelle.</p>
                    <div class="bg-blue-50 p-8 rounded-xl text-center mt-10"><p class="text-xl font-bold text-hrw-blue italic mb-2">"Vos pensées comptent. Votre voix compte. Votre honnêteté compte."</p></div>`,
                comp_1_title: "1. Essai Écrit", comp_2_title: "2. Lecture Audio", comp_3_title: "3. Réponse Orale",
                page_comp_title: "La Compétition",
                page_comp_desc: "La Compétition d'Essai et d'Expression Vocale HRW est conçue pour l'ère de l'IA. Au lieu de récompenser l'écriture mémorisée ou polie, nous reconnaissons la compréhension authentique et l'expression personnelle. Les étudiants soumettent un essai original plus deux courts enregistrements vocaux : une lecture de l'essai et une réponse spontanée. Ensemble, ceux-ci révèlent une réelle compréhension, appropriation et clarté — car votre voix compte plus qu'une écriture parfaite.",
                who_can_participate: "Qui Peut Participer",
                timeline_title: "Calendrier",
                time_open: "Ouverture", time_deadline: "Date Limite", time_finalists: "Finalistes", time_gala: "Gala",
                page_guide_title: "Directives Officielles",
                guide_body: `
                    <p class="mb-4">Hope Rising World (HRW) propose la Compétition d'Essai et d'Expression Vocale, un programme mondial tourné vers l'avenir et conçu pour l'ère de l'intelligence artificielle. Alors que l'IA peut générer des essais polis instantanément, elle ne peut pas remplacer la pensée authentique, la perspective vécue et la voix humaine d'un jeune.</p>
                    <p class="mb-4">Les participants accomplissent trois tâches connectées : (1) écrire un essai original basé sur une lecture fournie, (2) enregistrer une lecture audio de leur essai, et (3) soumettre une courte réponse orale spontanée. L'évaluation de l'écriture et de la voix permet à HRW d'honorer la sincérité, de renforcer l'intégrité et de mesurer la véritable compréhension de manière équitable.</p>
                    <p class="mb-4">La compétition HRW est ouverte aux jeunes du monde entier et accueille les anglophones natifs et non natifs. Notre message directeur est simple :</p>
                    <p class="font-bold text-hrw-blue text-xl italic">“Ne visez pas la perfection. Visez l'honnêteté.”</p>`,
                integrity_title: "Politique d'Intégrité",
                integrity_desc: "Interdiction stricte : L'utilisation d'outils d'IA pour écrire votre essai est strictement interdite.",
                rubric_header: "Critères de Notation", rubric_title: "Barème de Notation",
                footer_desc: "Autonomiser les jeunes grâce à l'expression authentique.",
                footer_resources: "Ressources", footer_contact: "Contact"
            },
            de: {
                nav_home: "Start", nav_competition: "Wettbewerb", nav_guidelines: "Richtlinien", nav_judge: "Jury-Portal", nav_submit: "Einreichen",
                hero_badge: "Globaler Wettbewerb 2026",
                hero_title: "Authentische Stimme im KI-Zeitalter",
                hero_subtitle: "In einer Welt, in der Technologie das Schreiben imitieren kann, feiert HRW das, was nicht automatisiert werden kann: menschliches Verständnis und aufrichtigen Ausdruck.",
                cta_start: "Einreichen Starten", cta_guide: "Leitfaden",
                about_title: "Über den Wettbewerb",
                about_body: `
                    <p class="mb-6">Hope Rising World (HRW) startet einen neuen globalen Bildungswettbewerb: den <strong>Essay & Voice Expression Competition</strong> – ein Programm, das entwickelt wurde, um das zu schützen und zu fördern, was beim Lernen junger Menschen am wichtigsten ist: Bedeutung, Integrität und authentische Stimme.</p>
                    <p class="mb-6">Traditionelle Essay-Wettbewerbe belohnen oft oberflächlichen Glanz und technische Flüssigkeit. In der heutigen Welt sind diese Signale zunehmend unzuverlässig. KI-Schreibwerkzeuge können in Sekunden ausgefeilte Essays erstellen, was es schwieriger macht, echte Urheberschaft zu identifizieren und Schüler zu ermutigen, wesentliche menschliche Fähigkeiten aufzubauen.</p>
                    <p class="mb-6">Der Wettbewerb von HRW führt ein integriertes Modell ein, das sowohl schriftlichen als auch gesprochenen Ausdruck bewertet, um echtes Verständnis hervorzuheben. Diese Struktur unterstützt Fairness und stärkt die Integrität, indem Juroren die Konsistenz zwischen Text und Stimme bewerten können. Sie schafft auch ein ermutigendes Umfeld: Akzent oder nicht-muttersprachliche Flüssigkeit werden nicht bestraft, wenn die Bedeutung klar ist; was zählt, sind Aufrichtigkeit, Klarheit und persönliche Interpretation.</p>
                    <div class="bg-blue-50 p-8 rounded-xl text-center mt-10"><p class="text-xl font-bold text-hrw-blue italic mb-2">"Deine Gedanken zählen. Deine Stimme zählt. Deine Ehrlichkeit zählt."</p></div>`,
                comp_1_title: "1. Schriftlicher Essay", comp_2_title: "2. Audio-Lesung", comp_3_title: "3. Mündliche Antwort",
                page_comp_title: "Der Wettbewerb",
                page_comp_desc: "Der HRW Essay & Voice Expression Competition ist für das KI-Zeitalter konzipiert. Anstatt auswendig gelerntes oder poliertes Schreiben zu belohnen, erkennen wir authentisches Verständnis und persönlichen Ausdruck an. Schüler reichen einen originalen Essay sowie zwei kurze Sprachaufnahmen ein: eine Essay-Lesung und eine spontane Antwort. Zusammen offenbaren diese echtes Verständnis, Eigenverantwortung und Klarheit – denn deine Stimme zählt mehr als perfektes Schreiben.",
                who_can_participate: "Wer Kann Teilnehmen",
                timeline_title: "Zeitplan",
                time_open: "Eröffnung", time_deadline: "Frist", time_finalists: "Finalisten", time_gala: "Preisverleihung",
                page_guide_title: "Offizielle Richtlinien",
                guide_body: `
                    <p class="mb-4">Hope Rising World (HRW) schlägt den Essay & Voice Expression Competition vor, ein zukunftsfähiges globales Programm für das Zeitalter der künstlichen Intelligenz. Während KI sofort polierte Essays erstellen kann, kann sie das authentische Denken, die gelebte Perspektive und die menschliche Stimme eines jungen Menschen nicht ersetzen.</p>
                    <p class="mb-4">Teilnehmer erledigen drei verbundene Aufgaben: (1) Schreiben eines originalen Essays basierend auf einer bereitgestellten Lektüre, (2) Aufnahme einer Audio-Lesung ihres Essays und (3) Einreichung einer kurzen spontanen mündlichen Antwort. Die Bewertung von Schreiben und Stimme ermöglicht es HRW, Aufrichtigkeit zu ehren, Integrität zu stärken und echtes Verständnis auf faire Weise zu messen.</p>
                    <p class="mb-4">Der HRW-Wettbewerb steht Jugendlichen weltweit offen und heißt Muttersprachler und Nicht-Muttersprachler willkommen. Unsere leitende Botschaft ist einfach:</p>
                    <p class="font-bold text-hrw-blue text-xl italic">“Ziele nicht auf Perfektion. Ziele auf Ehrlichkeit.”</p>`,
                integrity_title: "Integritätsrichtlinie",
                integrity_desc: "Strenge Untersagung: Die Verwendung von KI-Tools zum Schreiben Ihres Essays ist strengstens verboten.",
                rubric_header: "Bewertung", rubric_title: "Bewertungsrubrik",
                footer_desc: "Stärkung der Jugend durch authentischen Ausdruck.",
                footer_resources: "Ressourcen", footer_contact: "Kontakt"
            },
            ko: {
                nav_home: "홈", nav_competition: "대회 소개", nav_guidelines: "가이드라인", nav_judge: "심사 포털", nav_submit: "참가 신청",
                hero_badge: "2026 글로벌 대회",
                hero_title: "AI 시대의 진정한 목소리",
                hero_subtitle: "기술이 글쓰기를 흉내 낼 수 있는 세상에서, HRW는 자동화될 수 없는 인간의 이해와 진솔한 표현을 기념합니다.",
                cta_start: "참가 신청하기", cta_guide: "가이드 다운로드",
                about_title: "대회 정보",
                about_body: `
                    <p class="mb-6">Hope Rising World (HRW)는 새로운 글로벌 교육 대회인 <strong>에세이 & 보이스 표현력 대회</strong>를 시작합니다. 이 프로그램은 청소년 학습에서 가장 중요한 의미, 진정성, 그리고 진정한 목소리를 보호하고 높이기 위해 설계되었습니다.</p>
                    <p class="mb-6">전통적인 에세이 대회는 종종 표면적인 세련됨과 기술적 유창함을 보상합니다. 오늘날의 세계에서 그러한 신호는 점점 신뢰할 수 없게 되었습니다. AI 작문 도구는 정교한 에세이를 순식간에 생성할 수 있어, 진짜 저자를 식별하기 어렵게 만들고 학생들이 이해, 성찰, 표현이라는 필수적인 인간 기술을 구축하도록 장려하기 어렵게 만듭니다.</p>
                    <p class="mb-6">HRW의 대회는 진정한 이해를 강조하기 위해 문어체와 구어체 표현을 모두 평가하는 통합 모델을 도입합니다. 이 구조는 심사위원이 텍스트와 목소리 간의 일관성을 평가할 수 있게 하여 공정성을 지원하고 진정성을 강화합니다. 또한 학생들에게 격려가 되는 환경을 조성합니다: 의미가 명확하다면 억양이나 비원어민의 유창함은 감점되지 않습니다. 중요한 것은 진실성, 명확성, 그리고 개인적인 해석입니다.</p>
                    <div class="bg-blue-50 p-8 rounded-xl text-center mt-10"><p class="text-xl font-bold text-hrw-blue italic mb-2">"당신의 생각은 소중합니다. 당신의 목소리는 중요합니다. 당신의 정직함이 핵심입니다."</p></div>`,
                comp_1_title: "1. 에세이 작성", comp_2_title: "2. 음성 낭독", comp_3_title: "3. 즉흥 답변",
                page_comp_title: "대회 개요",
                page_comp_desc: "HRW 에세이 & 보이스 표현력 대회는 AI 시대를 위해 설계되었습니다. 암기되거나 다듬어진 글쓰기를 보상하는 대신, 우리는 진정한 이해와 개인적인 표현을 인정합니다. 학생들은 창작 에세이와 함께 에세이 낭독과 즉흥 답변이라는 두 가지 짧은 음성 녹음을 제출합니다. 이들이 함께 어우러져 진정한 이해, 주인의식, 명확성을 드러냅니다. 왜냐하면 완벽한 글쓰기보다 당신의 목소리가 더 중요하기 때문입니다.",
                who_can_participate: "참가 대상",
                timeline_title: "대회 일정",
                time_open: "접수 시작", time_deadline: "마감", time_finalists: "결선 진출자 발표", time_gala: "시상식",
                page_guide_title: "공식 가이드라인",
                guide_body: `
                    <p class="mb-4">Hope Rising World (HRW)는 인공지능 시대를 위해 설계된 미래 지향적 글로벌 프로그램인 에세이 & 보이스 표현력 대회를 제안합니다. AI가 세련된 에세이를 즉시 생성할 수 있지만, 청소년의 진정한 생각, 살아있는 관점, 인간의 목소리를 대체할 수는 없습니다. 이 대회는 초점을 '완벽한 글쓰기'에서 '진정한 이해와 개인적 표현'으로 전환합니다.</p>
                    <p class="mb-4">참가자들은 세 가지 연결된 과제를 수행합니다: (1) 제공된 읽기 자료를 바탕으로 창작 에세이 작성, (2) 에세이 낭독 녹음, (3) 짧은 즉흥 구술 답변 제출. 글쓰기와 목소리를 모두 평가함으로써 HRW는 공정하고 연령에 적합한 방식으로 진실성을 존중하고, 진정성을 강화하며, 진정한 이해를 측정할 수 있습니다.</p>
                    <p class="mb-4">HRW 대회는 전 세계 청소년에게 열려 있으며 원어민과 비원어민 영어 사용자 모두를 환영합니다. 우리의 핵심 메시지는 간단합니다:</p>
                    <p class="font-bold text-hrw-blue text-xl italic">“완벽함을 목표로 하지 마세요. 정직함을 목표로 하세요.”</p>`,
                integrity_title: "윤리 정책",
                integrity_desc: "엄격 금지: AI 도구를 사용하여 에세이를 작성하거나 목소리를 생성하는 것은 엄격히 금지됩니다.",
                rubric_header: "채점 기준", rubric_title: "채점표",
                footer_desc: "AI 시대, 진정성 있는 표현을 통해 청소년에게 힘을 실어줍니다.",
                footer_resources: "리소스", footer_contact: "연락처"
            },
            ja: {
                nav_home: "ホーム", nav_competition: "コンテスト", nav_guidelines: "ガイドライン", nav_judge: "審査ポータル", nav_submit: "提出開始",
                hero_badge: "グローバルコンテスト 2026",
                hero_title: "AI時代における真の声",
                hero_subtitle: "テクノロジーが文章を模倣できる世界で、HRWは自動化できないものを称えます：人間の理解、個人的な視点、そして誠実な表現。",
                cta_start: "提出を開始", cta_guide: "ガイドをダウンロード",
                about_title: "コンテストについて",
                about_body: `
                    <p class="mb-6">Hope Rising World (HRW)は、新しいグローバル教育コンテスト「<strong>エッセイ＆ボイス表現コンテスト</strong>」を開始します。これは、若者の学習において最も重要なもの、すなわち意味、誠実さ、そして真の声を保護し高めるために設計されたプログラムです。</p>
                    <p class="mb-6">従来のエッセイコンテストは、表面的な洗練さや技術的な流暢さを評価することがよくあります。今日の世界では、それらのシグナルはますます信頼できなくなっています。AIライティングツールは数秒で洗練されたエッセイを作成できるため、真の著者を特定することが難しくなり、学生に理解、考察、表現という不可欠な人間的スキルを構築するよう促すことがさらに難しくなっています。</p>
                    <p class="mb-6">HRWのコンテストは、書かれた表現と話された表現の両方を評価して真の理解を浮き彫りにする統合モデルを導入しています。この構造は、審査員がテキストと声の一貫性を評価できるようにすることで公平性を支え、誠実さを強化します。また、学生にとって励みとなる環境を作り出します。意味が明確であれば、アクセントや非ネイティブの流暢さは減点されません。重要なのは、誠実さ、明確さ、そして個人的な解釈です。</p>
                    <div class="bg-blue-50 p-8 rounded-xl text-center mt-10"><p class="text-xl font-bold text-hrw-blue italic mb-2">"あなたの考えは重要です。あなたの声は重要です。あなたの誠実さが大切です。"</p></div>`,
                comp_1_title: "1. エッセイ執筆", comp_2_title: "2. 音声朗読", comp_3_title: "3. 即興応答",
                page_comp_title: "コンテスト概要",
                page_comp_desc: "HRWエッセイ＆ボイス表現コンテストは、AI時代のために構築されました。暗記されたり洗練されたりした文章を評価するのではなく、私たちは真の理解と個人的な表現を認めます。学生は、オリジナルのエッセイに加えて、エッセイの朗読と即興の応答という2つの短い音声録音を提出します。これらを合わせることで、真の理解、主体性、明確さが明らかになります。なぜなら、あなたの声は完璧な文章よりも重要だからです。",
                who_can_participate: "参加資格",
                timeline_title: "スケジュール",
                time_open: "受付開始", time_deadline: "締切", time_finalists: "ファイナリスト発表", time_gala: "授賞式",
                page_guide_title: "公式ガイドライン",
                guide_body: `
                    <p class="mb-4">Hope Rising World (HRW)は、人工知能の時代のために設計された未来志向のグローバルプログラムであるエッセイ＆ボイス表現コンテストを提案します。AIは洗練されたエッセイを瞬時に生成できますが、若者の真の思考、生きた視点、人間の声を置き換えることはできません。このコンテストは、「完璧な文章」から真の理解と個人的な表現へと焦点を移します。</p>
                    <p class="mb-4">参加者は3つの関連するタスクを完了します：（1）提供された読み物に基づいてオリジナルのエッセイを書く、（2）エッセイの朗読を録音する、（3）短い即興の口頭応答を提出する。文章と声の両方を評価することで、HRWは誠実さを称え、完全性を強化し、公平で年齢に適した方法で真の理解を測定することができます。</p>
                    <p class="mb-4">HRWコンテストは世界中の若者に開かれており、ネイティブおよび非ネイティブの英語話者を歓迎します。私たちの指針となるメッセージはシンプルです：</p>
                    <p class="font-bold text-hrw-blue text-xl italic">“完璧を目指さないでください。誠実さを目指してください。”</p>`,
                integrity_title: "誠実性ポリシー",
                integrity_desc: "厳格な禁止：AIツールを使用してエッセイを作成することは厳格に禁止されています。",
                rubric_header: "採点基準", rubric_title: "採点ルーブリック",
                footer_desc: "AI時代における真の表現を通じて若者を支援します。",
                footer_resources: "リソース", footer_contact: "お問い合わせ"
            },
            hi: {
                nav_home: "मुख्य पृष्ठ", nav_competition: "प्रतियोगिता", nav_guidelines: "दिशानिर्देश", nav_judge: "जज पोर्टल", nav_submit: "शुरू करें",
                hero_badge: "वैश्विक प्रतियोगिता 2026",
                hero_title: "AI के युग में प्रामाणिक आवाज़",
                hero_subtitle: "ऐसी दुनिया में जहां तकनीक लेखन की नकल कर सकती है, HRW उसका जश्न मनाता है जिसे स्वचालित नहीं किया जा सकता: मानवीय समझ और ईमानदार अभिव्यक्ति।",
                cta_start: "सबमिशन शुरू करें", cta_guide: "गाइड डाउनलोड करें",
                about_title: "प्रतियोगिता के बारे में",
                about_body: `
                    <p class="mb-6">होप राइजिंग वर्ल्ड (HRW) एक नई वैश्विक शैक्षिक प्रतियोगिता शुरू कर रहा है: <strong>निबंध और स्वर अभिव्यक्ति प्रतियोगिता</strong>—एक कार्यक्रम जो युवाओं के सीखने में सबसे महत्वपूर्ण चीजों की रक्षा और उत्थान के लिए डिज़ाइन किया गया है: अर्थ, अखंडता और प्रामाणिक आवाज़।</p>
                    <p class="mb-6">पारंपरिक निबंध प्रतियोगिताएं अक्सर सतही चमक और तकनीकी प्रवाह को पुरस्कृत करती हैं। आज की दुनिया में, वे संकेत तेजी से अविश्वसनीय होते जा रहे हैं। AI लेखन उपकरण सेकंड में परिष्कृत निबंध तैयार कर सकते हैं, जिससे वास्तविक लेखक की पहचान करना कठिन हो जाता है और छात्रों को समझ, प्रतिबिंब और अभिव्यक्ति के आवश्यक मानवीय कौशल का निर्माण करने के लिए प्रोत्साहित करना और भी कठिन हो जाता है।</p>
                    <p class="mb-6">HRW की प्रतियोगिता एक एकीकृत मॉडल पेश करती है जो वास्तविक समझ को उजागर करने के लिए लिखित और मौखिक दोनों अभिव्यक्तियों का मूल्यांकन करती है। यह संरचना निष्पक्षता का समर्थन करती है और न्यायाधीशों को पाठ और आवाज़ के बीच स्थिरता का मूल्यांकन करने की अनुमति देकर अखंडता को मजबूत करती है। यह छात्रों के लिए एक उत्साहजनक वातावरण भी बनाता है: यदि अर्थ स्पष्ट है तो उच्चारण या गैर-मूल प्रवाह को दंडित नहीं किया जाता है; जो मायने रखता है वह है ईमानदारी, स्पष्टता और व्यक्तिगत व्याख्या।</p>
                    <div class="bg-blue-50 p-8 rounded-xl text-center mt-10"><p class="text-xl font-bold text-hrw-blue italic mb-2">"आपके विचार मायने रखते हैं। आपकी आवाज़ मायने रखती है। आपकी ईमानदारी मायने रखती है।"</p></div>`,
                comp_1_title: "1. लिखित निबंध", comp_2_title: "2. ऑडियो रीडिंग", comp_3_title: "3. मौखिक प्रतिक्रिया",
                page_comp_title: "प्रतियोगिता",
                page_comp_desc: "HRW निबंध और स्वर अभिव्यक्ति प्रतियोगिता AI युग के लिए बनाई गई है। रटे-रटाए या परिष्कृत लेखन को पुरस्कृत करने के बजाय, हम प्रामाणिक समझ और व्यक्तिगत अभिव्यक्ति को पहचानते हैं। छात्र एक मूल निबंध के साथ दो छोटी वॉयस रिकॉर्डिंग जमा करते हैं: एक निबंध पाठन और एक सहज प्रतिक्रिया। साथ में, ये वास्तविक समझ, स्वामित्व और स्पष्टता प्रकट करते हैं—क्योंकि आपकी आवाज़ पूर्ण लेखन से अधिक मायने रखती है।",
                who_can_participate: "कौन भाग ले सकता है",
                timeline_title: "समय सीमा",
                time_open: "सबमिशन शुरू", time_deadline: "अंतिम तिथि", time_finalists: "फाइनलिस्ट", time_gala: "पुरस्कार समारोह",
                page_guide_title: "आधिकारिक दिशानिर्देश",
                guide_body: `
                    <p class="mb-4">होप राइजिंग वर्ल्ड (HRW) निबंध और स्वर अभिव्यक्ति प्रतियोगिता का प्रस्ताव करता है, जो कृत्रिम बुद्धिमत्ता के युग के लिए डिज़ाइन किया गया एक भविष्य के लिए तैयार वैश्विक कार्यक्रम है। जबकि AI तुरंत परिष्कृत निबंध तैयार कर सकता है, यह एक युवा व्यक्ति की प्रामाणिक सोच, जीवित दृष्टिकोण और मानवीय आवाज़ की जगह नहीं ले सकता है। यह प्रतियोगिता "पूर्ण लेखन" से वास्तविक समझ और व्यक्तिगत अभिव्यक्ति पर ध्यान केंद्रित करती है।</p>
                    <p class="mb-4">प्रतिभागी तीन जुड़े हुए कार्यों को पूरा करते हैं: (1) प्रदान किए गए पाठ के आधार पर एक मूल निबंध लिखें, (2) अपने निबंध का ऑडियो पाठ रिकॉर्ड करें, और (3) एक छोटी सहज मौखिक प्रतिक्रिया प्रस्तुत करें। लेखन और आवाज़ दोनों का मूल्यांकन करने से HRW को ईमानदारी का सम्मान करने, अखंडता को मजबूत करने और निष्पक्ष, आयु-उपयुक्त तरीके से वास्तविक समझ को मापने की अनुमति मिलती है।</p>
                    <p class="mb-4">HRW प्रतियोगिता दुनिया भर के युवाओं के लिए खुली है और देशी और गैर-देशी अंग्रेजी बोलने वालों का स्वागत करती है। हमारा मार्गदर्शक संदेश सरल है:</p>
                    <p class="font-bold text-hrw-blue text-xl italic">“पूर्णता का लक्ष्य न रखें। ईमानदारी का लक्ष्य रखें।”</p>`,
                integrity_title: "ईमानदारी नीति",
                integrity_desc: "सख्त निषेध: निबंध लिखने के लिए AI टूल्स का उपयोग सख्त वर्जित है।",
                rubric_header: "स्कोरिंग", rubric_title: "स्कोरिंग रूब्रिक",
                footer_desc: "AI के युग में प्रामाणिक अभिव्यक्ति के माध्यम से युवाओं को सशक्त बनाना।",
                footer_resources: "संसाधन", footer_contact: "संपर्क"
            },
            pt: {
                nav_home: "Início", nav_competition: "Competição", nav_guidelines: "Diretrizes", nav_judge: "Portal de Juízes", nav_submit: "Iniciar",
                hero_badge: "Competição Global 2026",
                hero_title: "Voz Autêntica na Era da IA",
                hero_subtitle: "Em um mundo onde a tecnologia pode imitar a escrita, a HRW celebra o que não pode ser automatizado: a compreensão humana e a expressão sincera.",
                cta_start: "Iniciar Submissão", cta_guide: "Baixar Guia",
                about_title: "Sobre a Competição",
                about_body: `
                    <p class="mb-6">A Hope Rising World (HRW) está lançando uma nova competição educacional global: a <strong>Competição de Redação e Expressão de Voz</strong> — um programa projetado para proteger e elevar o que mais importa no aprendizado dos jovens: significado, integridade e voz autêntica.</p>
                    <p class="mb-6">As competições tradicionais de redação frequentemente recompensam o polimento superficial e a fluência técnica. No mundo de hoje, esses sinais são cada vez menos confiáveis. Ferramentas de escrita de IA podem gerar redações sofisticadas em segundos, tornando mais difícil identificar a autoria genuína e ainda mais difícil incentivar os alunos a desenvolver as habilidades humanas essenciais de compreensão, reflexão e expressão.</p>
                    <p class="mb-6">A competição da HRW introduz um modelo integrado que avalia tanto a expressão escrita quanto a falada para destacar a compreensão real. Essa estrutura apoia a justiça e fortalece a integridade, permitindo que os juízes avaliem a consistência entre texto e voz. Também cria um ambiente encorajador: sotaque ou fluência não nativa não são penalizados se o significado for claro; o que importa é a sinceridade, a clareza e a interpretação pessoal.</p>
                    <div class="bg-blue-50 p-8 rounded-xl text-center mt-10"><p class="text-xl font-bold text-hrw-blue italic mb-2">"Seus pensamentos importam. Sua voz importa. Sua honestidade importa."</p></div>`,
                comp_1_title: "1. Redação", comp_2_title: "2. Leitura de Áudio", comp_3_title: "3. Resposta Oral",
                page_comp_title: "A Competição",
                page_comp_desc: "A Competição de Redação e Expressão de Voz da HRW é construída para a era da IA. Em vez de recompensar a escrita memorizada ou polida, reconhecemos a compreensão autêntica e a expressão pessoal. Os alunos enviam uma redação original mais duas gravações de voz curtas: uma leitura da redação e uma resposta espontânea. Juntos, estes revelam compreensão real, propriedade e clareza — porque sua voz importa mais do que uma escrita perfeita.",
                who_can_participate: "Quem Pode Participar",
                timeline_title: "Cronograma",
                time_open: "Abertura", time_deadline: "Prazo Final", time_finalists: "Finalistas", time_gala: "Gala de Prêmios",
                page_guide_title: "Diretrizes Oficiais",
                guide_body: `
                    <p class="mb-4">A Hope Rising World (HRW) propõe a Competição de Redação e Expressão de Voz, um programa global pronto para o futuro projetado para a era da inteligência artificial. Embora a IA possa gerar redações polidas instantaneamente, ela não pode substituir o pensamento autêntico, a perspectiva vivida e a voz humana de um jovem. Esta competição muda o foco da "escrita perfeita" para a compreensão real e expressão pessoal.</p>
                    <p class="mb-4">Os participantes completam três tarefas conectadas: (1) escrever uma redação original com base em uma leitura fornecida, (2) gravar uma leitura de áudio de sua redação e (3) enviar uma resposta oral espontânea curta. Avaliar tanto a escrita quanto a voz permite à HRW honrar a sinceridade, fortalecer a integridade e medir a compreensão genuína de uma forma justa e adequada à idade.</p>
                    <p class="mb-4">A competição HRW está aberta a jovens em todo o mundo e acolhe falantes nativos e não nativos de inglês. Nossa mensagem orientadora é simples:</p>
                    <p class="font-bold text-hrw-blue text-xl italic">“Não busque a perfeição. Busque a honestidade.”</p>`,
                integrity_title: "Política de Integridade",
                integrity_desc: "Proibição Estrita: O uso de ferramentas de IA para escrever seu ensaio é estritamente proibido.",
                rubric_header: "Como Você é Avaliado", rubric_title: "Rubrica de Pontuação",
                footer_desc: "Empoderando jovens através da expressão autêntica na era da IA.",
                footer_resources: "Recursos", footer_contact: "Contato"
            },
            zh: {
                nav_home: "首页", nav_competition: "竞赛", nav_guidelines: "指南", nav_judge: "评委入口", nav_submit: "开始提交",
                hero_badge: "2026 全球竞赛",
                hero_title: "AI 时代的真实声音",
                hero_subtitle: "在一个技术可以模仿写作的世界里，HRW 颂扬那些无法自动化的东西：人类的理解、个人的视角和真诚的表达。",
                cta_start: "开始提交", cta_guide: "下载指南",
                about_title: "关于竞赛",
                about_body: `
                    <p class="mb-6">Hope Rising World (HRW) 正在推出一项新的全球教育竞赛：<strong>论文与声音表达竞赛</strong>——该项目旨在保护和提升年轻人在学习中最重要的东西：意义、正直和真实的声音。</p>
                    <p class="mb-6">传统的论文竞赛往往奖励表面的润色和技术上的流畅。在当今世界，这些信号越来越不可靠。AI 写作工具可以在几秒钟内生成复杂的论文，这使得识别真正的作者身份变得更加困难，也更难鼓励学生建立理解、反思和表达等基本的人类技能。</p>
                    <p class="mb-6">HRW 的竞赛引入了一种综合模型，评估书面和口头表达，以突出真实的理解。这种结构通过允许评委评估文本和声音之间的一致性来支持公平并加强正直。它还为学生创造了一个令人鼓舞的环境：如果意思清晰，口音或非母语的流利程度不会受到惩罚；重要的是真诚、清晰和个人解读。</p>
                    <div class="bg-blue-50 p-8 rounded-xl text-center mt-10"><p class="text-xl font-bold text-hrw-blue italic mb-2">"你的思想很重要。你的声音很重要。你的诚实很重要。"</p></div>`,
                comp_1_title: "1. 书面论文", comp_2_title: "2. 音频朗读", comp_3_title: "3. 即兴口语",
                page_comp_title: "竞赛详情",
                page_comp_desc: "HRW 论文与声音表达竞赛专为 AI 时代打造。我们不奖励死记硬背或润色过的写作，而是认可真实的理解和个人表达。学生提交一篇原创论文加上两段简短的语音录音：一段论文朗读和一段即兴回答。这两者共同揭示了真实的理解、自主权和清晰度——因为你的声音比完美的写作更重要。",
                who_can_participate: "谁可以参加",
                timeline_title: "竞赛时间表",
                time_open: "开始提交", time_deadline: "截止日期", time_finalists: "决赛入围", time_gala: "颁奖典礼",
                page_guide_title: "官方指南",
                guide_body: `
                    <p class="mb-4">Hope Rising World (HRW) 提出了论文与声音表达竞赛，这是一个为人工智能时代设计的面向未来的全球项目。虽然 AI 可以瞬间生成润色过的论文，但它无法取代年轻人真实的思考、亲身经历的视角和人类的声音。本次竞赛将焦点从“完美写作”转移到真实理解和个人表达上。</p>
                    <p class="mb-4">参与者完成三个相关联的任务：（1）根据提供的阅读材料撰写一篇原创论文，（2）录制一段论文朗读音频，以及（3）提交一段简短的即兴口头回答。评估写作和声音使 HRW 能够以公平、适合年龄的方式尊重真诚、加强正直并衡量真正的理解。</p>
                    <p class="mb-4">HRW 竞赛向全世界的青年开放，欢迎英语母语者和非母语者参加。我们的指导信息很简单：</p>
                    <p class="font-bold text-hrw-blue text-xl italic">“不要追求完美。追求诚实。”</p>`,
                integrity_title: "诚信政策",
                integrity_desc: "严禁：严禁使用 AI 工具撰写论文或生成语音。",
                rubric_header: "评分标准", rubric_title: "评分细则",
                footer_desc: "在 AI 时代通过真实表达赋予青年力量。",
                footer_resources: "资源", footer_contact: "联系方式"
            }
        };

        // --- LANGUAGE SWITCHER LOGIC ---
        let currentLang = 'en';

        function changeLanguage(lang) {
            currentLang = lang;
            const t = translations[lang];
            if (!t) return;

            // Update all elements with data-i18n attribute
            document.querySelectorAll('[data-i18n]').forEach(el => {
                const key = el.getAttribute('data-i18n');
                if (t[key]) {
                    // CHANGED to innerHTML to support formatted text (bold, paragraphs)
                    el.innerHTML = t[key];
                }
            });
            
            // Re-render current view to apply translations to dynamically loaded content
            // Note: simple re-render of current view if it's the active one
            // We can just call switchView again on the current ID, which re-injects HTML and re-runs changeLanguage
            // But to avoid loop, we just need to re-apply innerHTML which is handled above.
        }

        // --- VIEW MANAGEMENT ---
        let currentViewId = 'home';

        function switchView(viewName) {
            currentViewId = viewName;
            const container = document.getElementById('app-content');
            const template = document.getElementById(`view-${viewName}`);
            
            if (template) {
                container.innerHTML = template.innerHTML;
                lucide.createIcons();
                window.scrollTo(0, 0);

                // Re-apply translations to the new content
                changeLanguage(currentLang);
                
                // Update Select value
                document.getElementById('language-select').value = currentLang;

                if (viewName === 'submission') {
                    // Placeholder for submission logic
                }
            } else {
                console.error("View not found: " + viewName);
            }
        }

        // Initialize Home View
        window.onload = () => {
            switchView('home');
        };

        function renderStep(step) {
             // Logic removed for brevity
        }
    </script>
</body>
</html>
