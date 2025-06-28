<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Interactive Guide to Logo Design</title>
    <!-- Chosen Palette: Earthy Harmony -->
    <!-- Application Structure Plan: A thematic, single-page application with a sticky navigation bar for easy access to distinct sections. The structure is designed for non-linear exploration, allowing users to dive into specific topics like Principles, Types, Process, or Psychology as they wish. Key interactions include clickable cards to reveal detailed information, a tabbed interface for comparing logo types, an interactive timeline for history, and a dynamic radar chart for visualizing color psychology. This structure was chosen over a linear report format to make the dense information more digestible and engaging, promoting active learning and user-driven discovery. -->
    <!-- Visualization & Content Choices: 
        - Principles: Report Info -> 5 Principles of Design -> Goal: Inform/Compare -> Viz: Interactive Cards -> Interaction: Click-to-reveal -> Justification: Breaks down complex ideas into manageable, user-triggered chunks. -> Method: HTML/CSS/JS.
        - Logo Types: Report Info -> 7 Logo Types -> Goal: Organize/Compare -> Viz: Tabbed Gallery -> Interaction: Click tab to switch content -> Justification: Allows easy comparison between types without overwhelming the user. -> Method: HTML/CSS/JS.
        - Design Process: Report Info -> 7-Step Process -> Goal: Organize/Inform -> Viz: Interactive Vertical Timeline -> Interaction: Click step to expand -> Justification: Visualizes the process flow sequentially, which is more intuitive than a list. -> Method: HTML/CSS/JS.
        - Color Psychology: Report Info -> Color Meanings -> Goal: Explore/Inform -> Viz: Interactive Palette + Radar Chart -> Interaction: Hover/Click color to update chart and text -> Justification: Creates a "wow" factor and powerfully visualizes abstract emotional data. -> Method: Chart.js/Canvas + JS.
        - History: Report Info -> Historical Eras -> Goal: Show Change -> Viz: Interactive Horizontal Timeline -> Interaction: Click era to show details -> Justification: Chronological data is best presented on a timeline to show evolution. -> Method: HTML/CSS/JS.
        - Legal Info: Report Info -> Copyright vs. Trademark -> Goal: Compare/Inform -> Viz: Comparison Table -> Interaction: Static -> Justification: A table is the clearest way to compare two distinct legal concepts. -> Method: HTML/CSS.
        - CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. 
    -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F8F5F2;
            color: #3C3633;
        }
        h1, h2, h3 {
            font-family: 'Playfair Display', serif;
        }
        .nav-link {
            transition: color 0.3s, border-bottom-color 0.3s;
            border-bottom: 2px solid transparent;
        }
        .nav-link:hover, .nav-link.active {
            color: #A27B5C;
            border-bottom-color: #A27B5C;
        }
        .section-fade-in {
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.6s ease-out, transform 0.6s ease-out;
        }
        .section-fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
        .chart-container {
            position: relative;
            margin: auto;
            height: 40vh;
            max-height: 400px;
            width: 90vw;
            max-width: 500px;
        }
    </style>
</head>
<body class="antialiased">

    <!-- Header & Navigation -->
    <header class="bg-white/80 backdrop-blur-md sticky top-0 z-50 shadow-sm">
        <nav class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <div class="flex-shrink-0">
                    <h1 class="text-xl font-bold text-gray-800">Logo Design</h1>
                </div>
                <div class="hidden md:block">
                    <div class="ml-10 flex items-baseline space-x-4">
                        <a href="#principles" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-700">Principles</a>
                        <a href="#types" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-700">Types</a>
                        <a href="#process" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-700">Process</a>
                        <a href="#psychology" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-700">Psychology</a>
                        <a href="#history" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-700">History & Trends</a>
                        <a href="#legal" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-gray-700">Legal</a>
                    </div>
                </div>
                <div class="md:hidden">
                    <button id="mobile-menu-button" class="inline-flex items-center justify-center p-2 rounded-md text-gray-600 hover:text-gray-800 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-A27B5C">
                        <span class="sr-only">Open main menu</span>
                        <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
                        </svg>
                    </button>
                </div>
            </div>
        </nav>
        <div class="md:hidden hidden" id="mobile-menu">
            <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
                <a href="#principles" class="nav-link block px-3 py-2 rounded-md text-base font-medium text-gray-700">Principles</a>
                <a href="#types" class="nav-link block px-3 py-2 rounded-md text-base font-medium text-gray-700">Types</a>
                <a href="#process" class="nav-link block px-3 py-2 rounded-md text-base font-medium text-gray-700">Process</a>
                <a href="#psychology" class="nav-link block px-3 py-2 rounded-md text-base font-medium text-gray-700">Psychology</a>
                <a href="#history" class="nav-link block px-3 py-2 rounded-md text-base font-medium text-gray-700">History & Trends</a>
                <a href="#legal" class="nav-link block px-3 py-2 rounded-md text-base font-medium text-gray-700">Legal</a>
            </div>
        </div>
    </header>

    <main class="container mx-auto px-4 sm:px-6 lg:px-8 py-8 md:py-12">

        <!-- Hero Section -->
        <section id="home" class="text-center py-16 section-fade-in">
            <h1 class="text-4xl md:text-6xl font-bold tracking-tight">An Interactive Guide to Logo Design</h1>
            <p class="mt-6 max-w-3xl mx-auto text-lg text-gray-600">This experience translates a comprehensive report on logo design into an interactive journey. Explore the core principles, diverse types, creative process, and deep psychology behind crafting a powerful brand identity.</p>
        </section>

        <!-- Principles Section -->
        <section id="principles" class="py-16 section-fade-in">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold">Fundamental Principles</h2>
                <p class="mt-4 max-w-2xl mx-auto text-gray-600">Effective logo design is governed by five core principles. Click on each principle to understand its importance and how to apply it.</p>
            </div>
            <div id="principles-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-8">
                <!-- Principles will be dynamically inserted here -->
            </div>
        </section>

        <!-- Types Section -->
        <section id="types" class="py-16 bg-white rounded-2xl shadow-lg section-fade-in">
             <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold">The 7 Types of Logos</h2>
                <p class="mt-4 max-w-2xl mx-auto text-gray-600">From simple wordmarks to intricate emblems, each logo type serves a different strategic purpose. Select a type to explore its characteristics, strengths, and ideal use cases.</p>
            </div>
            <div class="flex flex-col lg:flex-row gap-8">
                <div class="lg:w-1/3">
                    <div id="logo-types-tabs" class="flex flex-row lg:flex-col flex-wrap justify-center gap-2">
                         <!-- Tabs will be dynamically inserted here -->
                    </div>
                </div>
                <div id="logo-types-content" class="lg:w-2/3 p-6 bg-gray-50 rounded-lg min-h-[300px]">
                    <!-- Content will be dynamically inserted here -->
                </div>
            </div>
        </section>
        
        <!-- Process Section -->
        <section id="process" class="py-16 section-fade-in">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-bold">The Professional Design Process</h2>
                <p class="mt-4 max-w-2xl mx-auto text-gray-600">Creating a logo is a systematic, 7-step journey from strategic discovery to final delivery. Click each step to uncover the key activities involved.</p>
            </div>
            <div id="process-timeline" class="relative max-w-4xl mx-auto">
                <!-- Timeline line -->
                <div class="absolute left-1/2 -translate-x-1/2 h-full w-0.5 bg-gray-300"></div>
                <!-- Timeline items will be dynamically inserted here -->
            </div>
        </section>
        
        <!-- Psychology Section -->
        <section id="psychology" class="py-16 bg-white rounded-2xl shadow-lg section-fade-in">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold">The Psychology of Design</h2>
                <p class="mt-4 max-w-2xl mx-auto text-gray-600">Logos are powerful psychological tools. Explore how color and shape influence perception and emotion. Hover over a color to see its associated traits visualized.</p>
            </div>
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
                <div>
                    <h3 class="text-2xl font-bold mb-4 text-center">Color Psychology</h3>
                    <div id="color-palette" class="flex flex-wrap justify-center gap-3 mb-6">
                        <!-- Color swatches will be inserted here -->
                    </div>
                    <div id="color-info" class="text-center p-4 bg-gray-50 rounded-lg">
                        <h4 id="color-name" class="font-bold text-lg">Select a Color</h4>
                        <p id="color-meaning" class="text-gray-600">Hover over a color to learn its meaning.</p>
                    </div>
                </div>
                <div class="chart-container">
                    <canvas id="color-psychology-chart"></canvas>
                </div>
            </div>
            <div class="mt-16">
                <h3 class="text-2xl font-bold mb-8 text-center">Shape Psychology</h3>
                <div id="shape-psychology-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-6 text-center">
                    <!-- Shapes will be inserted here -->
                </div>
            </div>
        </section>

        <!-- History & Trends Section -->
        <section id="history" class="py-16 section-fade-in">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold">History & Future Trends</h2>
                <p class="mt-4 max-w-2xl mx-auto text-gray-600">Logo design reflects the evolution of society and technology. Journey through its history and explore the trends shaping its future.</p>
            </div>
            
            <!-- History Timeline -->
            <div>
                <h3 class="text-2xl font-bold mb-8 text-center">A Timeline of Logo Design</h3>
                <div class="relative">
                    <div class="absolute top-1/2 -translate-y-1/2 w-full h-0.5 bg-gray-300"></div>
                    <div id="history-timeline" class="relative flex justify-between">
                         <!-- History items will be inserted here -->
                    </div>
                </div>
                <div id="history-content" class="mt-8 p-6 bg-gray-50 rounded-lg min-h-[150px]">
                    <!-- History content will be displayed here -->
                </div>
            </div>

            <!-- Future Trends -->
            <div class="mt-20">
                 <h3 class="text-2xl font-bold mb-8 text-center">Future Trends (2025)</h3>
                 <div id="trends-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- Trends will be inserted here -->
                 </div>
            </div>
        </section>
        
        <!-- Legal Section -->
        <section id="legal" class="py-16 bg-white rounded-2xl shadow-lg section-fade-in">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold">Legal Protection</h2>
                <p class="mt-4 max-w-2xl mx-auto text-gray-600">A logo is a valuable asset. Understand the difference between Copyright and Trademark and learn how to protect your brand identity.</p>
            </div>
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <div id="legal-comparison">
                     <!-- Legal comparison table will be inserted here -->
                </div>
                <div>
                    <h3 class="text-2xl font-bold mb-4">5 Essential Steps for Protection</h3>
                    <ul id="legal-steps" class="space-y-4">
                        <!-- Legal steps list will be inserted here -->
                    </ul>
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-gray-800 text-white mt-16">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8 py-8 text-center">
            <p>An Interactive Exploration of Logo Design</p>
            <p class="text-sm text-gray-400 mt-2">Transforming comprehensive analysis into an engaging experience.</p>
        </div>
    </footer>


<script>
document.addEventListener('DOMContentLoaded', () => {

    const appData = {
        principles: [
            { name: "Simplicity", benefit: "Quick recognition, cuts through noise, easily scalable, memorable.", action: "Focus on the core message, strip away unnecessary elements, and test in black and white." },
            { name: "Memorability", benefit: "Sticks in people's minds, ensures brand stays top-of-mind, stands out.", action: "Aim for uniqueness using unique shapes, colors, or clever use of negative space." },
            { name: "Appropriateness", benefit: "Communicates the right tone/feel, appeals to the target audience, aligns with brand values.", action: "Research the industry, audience, and competitors. Avoid clichés." },
            { name: "Versatility", benefit: "Ensures consistent branding across all platforms, effective in all sizes and mediums.", action: "Design with adaptability in mind. Use a vector format and test in various sizes and colors." },
            { name: "Timelessness", benefit: "Ensures the brand remains relevant for years, avoiding frequent, costly redesigns.", action: "Avoid overly trendy fonts or elements, focusing instead on classic shapes and enduring concepts." }
        ],
        logoTypes: [
            { name: "Wordmark", characteristics: "Company name styled in a unique font.", strengths: "Excellent brand name recognition, simplicity, versatility.", bestUse: "Concise, distinctive names; new businesses establishing presence." },
            { name: "Lettermark", characteristics: "Initials or acronym of a brand.", strengths: "High versatility at tiny sizes (favicons), conveys professionalism.", bestUse: "Long or hard-to-pronounce names; when acronyms are common." },
            { name: "Pictorial Mark", characteristics: "Icon or graphic element only.", strengths: "Iconic brand presence, transcends language barriers.", bestUse: "Established brands with high recognition; strong visual associations." },
            { name: "Abstract Mark", characteristics: "Abstract geometric form representing the business.", strengths: "Creates a unique image, condenses brand conceptually, effective globally.", bestUse: "Conveying abstract brand values; requires professional design execution." },
            { name: "Mascot Logo", characteristics: "Illustrated character or figure.", strengths: "Brings brand to life, creates a friendly, approachable persona.", bestUse: "Brands targeting young children or families." },
            { name: "Combination Mark", characteristics: "Wordmark/lettermark combined with a symbol/mascot.", strengths: "Best of both worlds (visual recognition + name reinforcement).", bestUse: "New brands needing both name and symbol; versatile branding." },
            { name: "Emblem", characteristics: "Typography within a symbol or icon (badge/seal/crest).", strengths: "Exudes a traditional aesthetic, creates a powerful impression.", bestUse: "Schools, organizations, government agencies, auto industry." }
        ],
        process: [
            { stage: "1. Discovery & Evaluation", activity: "Understand client business, history, industry, competitors, and target audience; define brand identity, voice, values, and goals through questionnaires/workshops." },
            { stage: "2. Research", activity: "Analyze industry trends and competitive landscape; identify opportunities for differentiation; determine all intended logo applications (e.g., social media, print)." },
            { stage: "3. Brainstorming & Sketching", activity: "Translate insights into visual concepts; use techniques like mind mapping; sketch a wide variety of logo ideas to explore possibilities rapidly." },
            { stage: "4. Digital Execution", activity: "Transform selected concepts into refined digital drafts using vector software; refine details, ensure alignment, and finalize color schemes." },
            { stage: "5. Refinement & Feedback", activity: "Continuously improve the design based on constructive input from the team, stakeholders, and potential customers to ensure broad resonance." },
            { stage: "6. Presentation & Approval", activity: "Effectively showcase logo concepts to the client with a clear design rationale; secure final approval for the chosen design." },
            { stage: "7. Delivery", activity: "Export final logo files in all necessary formats and create a comprehensive style guide outlining usage rules, color palettes, and typography." }
        ],
        psychology: {
            colors: [
                { name: 'Red', hex: '#E74C3C', values: { Passion: 9, Energy: 8, Power: 7, Danger: 6, Confidence: 7 } },
                { name: 'Orange', hex: '#E67E22', values: { Friendly: 8, Cheerful: 9, Confidence: 6, Energy: 7, Optimism: 9 } },
                { name: 'Yellow', hex: '#F1C40F', values: { Happiness: 9, Optimism: 8, Youthful: 7, Warning: 5, Fun: 8 } },
                { name: 'Green', hex: '#2ECC71', values: { Growth: 9, Nature: 10, Harmony: 8, Wealth: 7, Peace: 8 } },
                { name: 'Blue', hex: '#3498DB', values: { Trust: 9, Calm: 8, Security: 9, Intelligence: 7, Professional: 8 } },
                { name: 'Purple', hex: '#9B59B6', values: { Royalty: 9, Luxury: 8, Wisdom: 7, Creativity: 9, Fantasy: 7 } },
                { name: 'Black', hex: '#2C3E50', values: { Power: 9, Elegance: 9, Sophistication: 8, Formality: 7, Mystery: 6 } },
                { name: 'White', hex: '#ECF0F1', values: { Purity: 9, Simplicity: 10, Cleanliness: 9, Peace: 7, Modern: 8 } }
            ],
            shapes: [
                { name: "Circle", meaning: "Community, unity, wholeness; friendly and approachable.", icon: `<div class="w-16 h-16 rounded-full bg-gray-300 mx-auto"></div>` },
                { name: "Square", meaning: "Stability, structure, order, and professionalism.", icon: `<div class="w-16 h-16 bg-gray-300 mx-auto"></div>` },
                { name: "Triangle", meaning: "Energy, action, direction, and power.", icon: `<div class="w-0 h-0 border-l-8 border-l-transparent border-r-8 border-r-transparent border-b-[16px] border-b-gray-300 scale-[4] mx-auto"></div>` },
                { name: "Curved Lines", meaning: "Fluidity, flexibility, and an organic, natural feel.", icon: `<svg class="w-16 h-16 mx-auto" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M10 90 Q 50 10, 90 90" stroke="#9ca3af" stroke-width="8" stroke-linecap="round"/></svg>` },
                { name: "Spiral", meaning: "Evolution, growth, expansion, and creativity.", icon: `<svg class="w-16 h-16 mx-auto" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M50 50 m -40, 0 a 40,40 0 1,0 80,0 a 40,40 0 1,0 -80,0 M50 50 m -30, 0 a 30,30 0 1,0 60,0 a 30,30 0 1,0 -60,0" stroke="#9ca3af" stroke-width="8"/></svg>` }
            ]
        },
        history: [
            { era: "Victorian (1837-1901)", description: "Characterized by heavy ornamentation, symmetrical layouts, and elaborate decorative elements with a focus on form." },
            { era: "Early Modern (1910-1935)", description: "A rebellion against tradition, embracing geometric, minimalist approaches and prioritizing function over form." },
            { era: "Heroic Realism (1934-1945)", description: "A propaganda style using realistic, idealized figures to educate and inspire a sense of duty and devotion." },
            { era: "Post Modern (1975-1990)", description: "Deliberately broke the rules of modernism, re-establishing interest in ornamentation, wit, and unconventional colors." },
            { era: "Minimalism (2001-Present)", description: "Dominant modern style using pared-down elements, simple forms, and flat colors, ideal for digital efficiency." }
        ],
        trends: [
            { name: "Minimalism", description: "Clean, straightforward designs that enhance clarity and scalability." },
            { name: "Animated/Interactive Logos", description: "Dynamic logos that engage audiences in unique, memorable digital experiences." },
            { name: "UX Integration", description: "Responsive logos that adapt to screen sizes and enhance the user journey." },
            { name: "Playful Typography", description: "Use of custom, hand-drawn, or unconventional fonts to infuse personality." },
            { name: "Eco-Conscious Themes", description: "Designs featuring natural elements and earthy tones to reflect sustainability." },
            { name: "Gradients & Vibrant Colors", description: "Adds depth, energy, and dynamism, making logos visually striking." },
            { name: "Mix and Match Type", description: "Deliberately using mismatched letters for an informal, attention-grabbing style." },
            { name: "Subtle Icons", description: "Ingeniously transforming letters into icons for a simple yet distinctive design." },
            { name: "Etched Emblems", description: "Emblem logos with intricate, hand-drawn marks for a traditional, artisanal feel." },
        ],
        legal: {
            comparison: [
                { feature: "Definition", copyright: "Protects original creative works (artistic elements).", trademark: "Protects symbols, names, and slogans distinguishing goods/services." },
                { feature: "Protection", copyright: "Automatic upon creation.", trademark: "Requires registration for strong protection." },
                { feature: "Scope", copyright: "Rights to reproduce, display, distribute. Doesn't cover the idea.", trademark: "Exclusive rights to use in connection with specific goods/services." },
                { feature: "Best For", copyright: "Protecting the artistic expression of the logo.", trademark: "Protecting the commercial brand identity in the marketplace." },
            ],
            steps: [
                { step: "Conduct a Trademark Search", description: "Ensure your design doesn't infringe on existing trademarks to avoid costly legal disputes." },
                { step: "Register Your Trademark", description: "Promptly register with the relevant IP office for exclusive rights and a strong legal deterrent." },
                { step: "Use Copyright Notices", description: "Incorporate a notice (e.g., ©) to signal your commitment to protecting your IP." },
                { step: "Draft Clear Contracts", description: "Use well-drafted agreements with designers to clarify ownership and usage rights." },
                { step: "Monitor and Enforce", description: "Regularly monitor the market for infringements and take swift legal action to protect your brand." },
            ]
        }
    };
    
    function initPrinciples() {
        const grid = document.getElementById('principles-grid');
        appData.principles.forEach(p => {
            const card = document.createElement('div');
            card.className = 'p-6 bg-white rounded-lg shadow-md cursor-pointer hover:shadow-xl hover:-translate-y-1 transition-all duration-300';
            card.innerHTML = `
                <h3 class="text-xl font-bold mb-2">${p.name}</h3>
                <div class="principle-details hidden text-gray-600">
                    <p class="font-semibold text-gray-700 mb-2">${p.benefit}</p>
                    <p>${p.action}</p>
                </div>
            `;
            grid.appendChild(card);

            card.addEventListener('click', () => {
                const details = card.querySelector('.principle-details');
                details.classList.toggle('hidden');
            });
        });
    }

    function initLogoTypes() {
        const tabsContainer = document.getElementById('logo-types-tabs');
        const contentContainer = document.getElementById('logo-types-content');
        
        appData.logoTypes.forEach((type, index) => {
            const tab = document.createElement('button');
            tab.className = 'w-full lg:w-auto text-left px-4 py-3 rounded-md font-semibold transition-colors duration-300';
            tab.textContent = type.name;
            tab.dataset.index = index;
            if (index === 0) {
                tab.classList.add('bg-gray-800', 'text-white');
            } else {
                tab.classList.add('bg-gray-200', 'text-gray-700', 'hover:bg-gray-300');
            }
            tabsContainer.appendChild(tab);

            tab.addEventListener('click', () => {
                // Update tab styles
                tabsContainer.querySelectorAll('button').forEach(t => {
                    t.classList.remove('bg-gray-800', 'text-white');
                    t.classList.add('bg-gray-200', 'text-gray-700', 'hover:bg-gray-300');
                });
                tab.classList.remove('bg-gray-200', 'hover:bg-gray-300');
                tab.classList.add('bg-gray-800', 'text-white');
                
                // Update content
                updateLogoTypeContent(index);
            });
        });
        updateLogoTypeContent(0); // Initial content
    }

    function updateLogoTypeContent(index) {
        const contentContainer = document.getElementById('logo-types-content');
        const type = appData.logoTypes[index];
        contentContainer.innerHTML = `
            <h3 class="text-2xl font-bold mb-4">${type.name}</h3>
            <p class="text-gray-600 mb-4">${type.characteristics}</p>
            <div class="space-y-3">
                <p><strong class="font-semibold text-gray-800">Strengths:</strong> ${type.strengths}</p>
                <p><strong class="font-semibold text-gray-800">Best For:</strong> ${type.bestUse}</p>
            </div>
        `;
    }

    function initProcess() {
        const timeline = document.getElementById('process-timeline');
        appData.process.forEach((item, index) => {
            const isLeft = index % 2 === 0;
            const timelineItem = document.createElement('div');
            timelineItem.className = `mb-8 flex justify-between items-center w-full ${isLeft ? 'flex-row-reverse' : ''}`;
            timelineItem.innerHTML = `
                <div class="order-1 w-5/12"></div>
                <div class="z-20 flex items-center order-1 bg-gray-800 shadow-xl w-8 h-8 rounded-full">
                    <h1 class="mx-auto font-semibold text-lg text-white">${index + 1}</h1>
                </div>
                <div class="order-1 bg-white rounded-lg shadow-xl w-5/12 px-6 py-4 cursor-pointer hover:bg-gray-50 transition">
                    <h3 class="mb-3 font-bold text-gray-800 text-lg">${item.stage}</h3>
                    <p class="text-sm leading-snug tracking-wide text-gray-600 text-opacity-100 hidden process-detail">${item.activity}</p>
                </div>
            `;
            timeline.appendChild(timelineItem);
            
            timelineItem.querySelector('.order-1.bg-white').addEventListener('click', (e) => {
                e.currentTarget.querySelector('.process-detail').classList.toggle('hidden');
            });
        });
    }

    let colorChart;
    function initPsychology() {
        const paletteContainer = document.getElementById('color-palette');
        const colorNameEl = document.getElementById('color-name');
        const colorMeaningEl = document.getElementById('color-meaning');

        appData.psychology.colors.forEach(color => {
            const swatch = document.createElement('div');
            swatch.className = 'w-10 h-10 rounded-full cursor-pointer shadow-md hover:scale-110 transition-transform';
            swatch.style.backgroundColor = color.hex;
            swatch.dataset.name = color.name;
            paletteContainer.appendChild(swatch);
            
            swatch.addEventListener('mouseover', () => {
                const selectedColor = appData.psychology.colors.find(c => c.name === color.name);
                colorNameEl.textContent = selectedColor.name;
                colorMeaningEl.textContent = Object.keys(selectedColor.values).join(', ');
                updateColorChart(selectedColor);
            });
        });

        const shapeGrid = document.getElementById('shape-psychology-grid');
        appData.psychology.shapes.forEach(shape => {
            const card = document.createElement('div');
            card.className = 'p-4 bg-white rounded-lg shadow-md';
            card.innerHTML = `
                <div class="h-20 flex items-center justify-center mb-2">${shape.icon}</div>
                <h4 class="font-bold text-md mb-1">${shape.name}</h4>
                <p class="text-sm text-gray-500">${shape.meaning}</p>
            `;
            shapeGrid.appendChild(card);
        });

        const ctx = document.getElementById('color-psychology-chart').getContext('2d');
        const initialColor = appData.psychology.colors[4];
        colorChart = new Chart(ctx, {
            type: 'radar',
            data: {
                labels: Object.keys(initialColor.values),
                datasets: [{
                    label: initialColor.name,
                    data: Object.values(initialColor.values),
                    backgroundColor: 'rgba(52, 152, 219, 0.2)',
                    borderColor: 'rgba(52, 152, 219, 1)',
                    borderWidth: 2,
                    pointBackgroundColor: 'rgba(52, 152, 219, 1)'
                }]
            },
            options: {
                maintainAspectRatio: false,
                scales: {
                    r: {
                        angleLines: { color: 'rgba(0, 0, 0, 0.1)' },
                        grid: { color: 'rgba(0, 0, 0, 0.1)' },
                        pointLabels: { font: { size: 12 }, color: '#3C3633' },
                        ticks: {
                            display: false,
                            beginAtZero: true,
                            max: 10
                        }
                    }
                },
                plugins: {
                    legend: {
                        display: false
                    }
                }
            }
        });
        updateColorChart(initialColor);
    }
    
    function updateColorChart(color) {
        colorChart.data.labels = Object.keys(color.values);
        colorChart.data.datasets[0].label = color.name;
        colorChart.data.datasets[0].data = Object.values(color.values);
        
        // Convert hex to rgba for chart colors
        const r = parseInt(color.hex.slice(1, 3), 16);
        const g = parseInt(color.hex.slice(3, 5), 16);
        const b = parseInt(color.hex.slice(5, 7), 16);

        colorChart.data.datasets[0].backgroundColor = `rgba(${r}, ${g}, ${b}, 0.2)`;
        colorChart.data.datasets[0].borderColor = `rgba(${r}, ${g}, ${b}, 1)`;
        colorChart.data.datasets[0].pointBackgroundColor = `rgba(${r}, ${g}, ${b}, 1)`;
        
        colorChart.update();
    }
    
    function initHistoryAndTrends() {
        const timeline = document.getElementById('history-timeline');
        const contentContainer = document.getElementById('history-content');

        appData.history.forEach((item, index) => {
            const dot = document.createElement('button');
            dot.className = 'history-dot z-10 w-6 h-6 rounded-full bg-gray-400 hover:bg-gray-800 transition-colors border-4 border-F8F5F2';
            dot.dataset.index = index;
            timeline.appendChild(dot);

            dot.addEventListener('click', () => {
                timeline.querySelectorAll('.history-dot').forEach(d => d.classList.replace('bg-gray-800', 'bg-gray-400'));
                dot.classList.replace('bg-gray-400', 'bg-gray-800');
                updateHistoryContent(index);
            });
        });

        // Activate first dot and show initial content
        timeline.querySelector('.history-dot').classList.replace('bg-gray-400', 'bg-gray-800');
        updateHistoryContent(0);

        const trendsGrid = document.getElementById('trends-grid');
        appData.trends.forEach(trend => {
            const card = document.createElement('div');
            card.className = 'p-6 bg-white rounded-lg shadow-md';
            card.innerHTML = `
                <h4 class="text-lg font-bold mb-2">${trend.name}</h4>
                <p class="text-gray-600">${trend.description}</p>
            `;
            trendsGrid.appendChild(card);
        });
    }

    function updateHistoryContent(index) {
        const contentContainer = document.getElementById('history-content');
        const item = appData.history[index];
        contentContainer.innerHTML = `
            <h4 class="font-bold text-xl mb-2 text-center">${item.era}</h4>
            <p class="text-gray-600 text-center">${item.description}</p>
        `;
    }

    function initLegal() {
        const comparisonContainer = document.getElementById('legal-comparison');
        const stepsContainer = document.getElementById('legal-steps');

        let tableHTML = `
            <table class="w-full border-collapse">
                <thead>
                    <tr>
                        <th class="p-3 font-bold uppercase bg-gray-200 text-gray-600 border border-gray-300 hidden lg:table-cell">Feature</th>
                        <th class="p-3 font-bold uppercase bg-gray-200 text-gray-600 border border-gray-300 hidden lg:table-cell">Copyright</th>
                        <th class="p-3 font-bold uppercase bg-gray-200 text-gray-600 border border-gray-300 hidden lg:table-cell">Trademark</th>
                    </tr>
                </thead>
                <tbody>`;

        appData.legal.comparison.forEach(row => {
            tableHTML += `
                <tr class="bg-white lg:hover:bg-gray-100 flex lg:table-row flex-row lg:flex-row flex-wrap lg:flex-no-wrap mb-10 lg:mb-0">
                    <td class="w-full lg:w-auto p-3 text-gray-800 text-center border border-b block lg:table-cell relative lg:static">
                        <span class="lg:hidden absolute top-0 left-0 bg-gray-200 px-2 py-1 text-xs font-bold uppercase">Feature</span>
                        ${row.feature}
                    </td>
                    <td class="w-full lg:w-auto p-3 text-gray-800 border border-b text-center block lg:table-cell relative lg:static">
                        <span class="lg:hidden absolute top-0 left-0 bg-gray-200 px-2 py-1 text-xs font-bold uppercase">Copyright</span>
                        ${row.copyright}
                    </td>
                    <td class="w-full lg:w-auto p-3 text-gray-800 border border-b text-center block lg:table-cell relative lg:static">
                        <span class="lg:hidden absolute top-0 left-0 bg-gray-200 px-2 py-1 text-xs font-bold uppercase">Trademark</span>
                        ${row.trademark}
                    </td>
                </tr>
            `;
        });
        tableHTML += `</tbody></table>`;
        comparisonContainer.innerHTML = tableHTML;

        appData.legal.steps.forEach((step, index) => {
            const item = document.createElement('li');
            item.className = "flex items-start";
            item.innerHTML = `
                <div class="flex-shrink-0 w-8 h-8 bg-gray-800 text-white rounded-full flex items-center justify-center font-bold mr-4">${index + 1}</div>
                <div>
                    <h4 class="font-bold">${step.step}</h4>
                    <p class="text-gray-600">${step.description}</p>
                </div>
            `;
            stepsContainer.appendChild(item);
        });
    }

    function initMobileMenu() {
        const button = document.getElementById('mobile-menu-button');
        const menu = document.getElementById('mobile-menu');
        button.addEventListener('click', () => {
            menu.classList.toggle('hidden');
        });
        // Close menu when a link is clicked
        menu.querySelectorAll('a').forEach(link => {
            link.addEventListener('click', () => {
                menu.classList.add('hidden');
            });
        });
    }

    function initScrollAnimations() {
        const sections = document.querySelectorAll('.section-fade-in');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                    observer.unobserve(entry.target);
                }
            });
        }, { threshold: 0.1 });

        sections.forEach(section => {
            observer.observe(section);
        });
        
        // Make hero section visible on load
        document.getElementById('home').classList.add('visible');
    }
    
    function initActiveNav() {
        const sections = document.querySelectorAll('section');
        const navLinks = document.querySelectorAll('.nav-link');

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    navLinks.forEach(link => {
                        link.classList.remove('active');
                        if (link.getAttribute('href').substring(1) === entry.target.id) {
                            link.classList.add('active');
                        }
                    });
                }
            });
        }, { rootMargin: '-50% 0px -50% 0px' });

        sections.forEach(section => {
            observer.observe(section);
        });
    }

    // Initialize all modules
    initPrinciples();
    initLogoTypes();
    initProcess();
    initPsychology();
    initHistoryAndTrends();
    initLegal();
    initMobileMenu();
    initScrollAnimations();
    initActiveNav();
});
</script>
</body>
</html>
