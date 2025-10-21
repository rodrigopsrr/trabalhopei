<!DOCTYPE html>
<html lang="pt-BR" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>O Corpo como Capital Simbólico na Empregabilidade</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Calm Harmony (Stone, Teal, Rose) -->
    <!-- Application Structure Plan: A thematic, single-page journey designed for exploration rather than linear reading. The structure flows from a broad introduction of the core concept ('Capital Simbólico') to more specific analyses (gendered pressures, impact by sector), and finally provides deeper academic context ('Conceitos-Chave'). This top-down approach allows users to grasp the main idea first and then delve into the nuances. A sticky navigation facilitates jumping between these thematic sections, supporting a non-linear user flow. This is more effective than a traditional report format because it breaks down a complex sociological topic into digestible, interactive modules, fostering engagement and understanding. -->
    <!-- Visualization & Content Choices: 
        1.  Gendered Pressures: Report Info -> Different aesthetic standards for men/women. Goal -> Compare. Viz -> Interactive Horizontal Bar Chart. Interaction -> Buttons toggle between 'Women' and 'Men' data sets, dynamically updating the chart and a descriptive text block. Justification -> A direct visual comparison of perceived pressures is more impactful than text alone. The toggle interaction actively engages the user in the comparison. Library -> Chart.js.
        2.  Impact by Sector: Report Info -> Aesthetic importance varies by industry. Goal -> Compare/Organize. Viz -> Interactive Radar Chart. Interaction -> Buttons filter the chart data by sector. Justification -> A radar chart effectively displays multi-variable data for a single entity (the sector), creating a clear "pressure profile" that is easy to compare visually. The filtering empowers the user to explore the data that is most relevant to them. Library -> Chart.js.
        3.  Key Concepts: Report Info -> Definitions of sociological terms (Capital Simbólico, Habitus). Goal -> Inform. Method -> Accordion Component. Interaction -> Clicking a term expands to show its definition. Justification -> An accordion organizes dense, academic information cleanly, preventing cognitive overload and allowing users to focus on one concept at a time. Method -> HTML/CSS/JS. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F5F5F4; 
            color: #292524; 
        }
        .nav-link.active {
            color: #0d9488;
            font-weight: 600;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
            height: 320px;
            max-height: 40vh;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }
        .accordion-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease-out;
        }
        .accordion-item.active .accordion-content {
            max-height: 500px; 
            transition: max-height 0.5s ease-in;
        }
        .accordion-item.active .accordion-arrow {
            transform: rotate(180deg);
        }
        .accordion-arrow {
            transition: transform 0.3s ease-out;
        }
        .btn-filter {
            transition: all 0.2s ease-in-out;
        }
        .btn-filter.active {
            background-color: #0d9488;
            color: white;
            transform: scale(1.05);
        }
    </style>
</head>
<body class="bg-stone-100 text-stone-800">

    <header class="bg-stone-100/80 backdrop-blur-sm sticky top-0 z-50 shadow-sm">
        <nav class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <div class="flex-shrink-0">
                    <h1 class="text-lg font-bold text-teal-700">Análise Estética & Trabalho</h1>
                </div>
                <div class="hidden md:block">
                    <div class="ml-10 flex items-baseline space-x-4">
                        <a href="#introducao" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-stone-600 hover:text-teal-700">Introdução</a>
                        <a href="#criterio-velado" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-stone-600 hover:text-teal-700">O Critério Velado</a>
                        <a href="#genero" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-stone-600 hover:text-teal-700">Pressões de Gênero</a>
                        <a href="#setores" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-stone-600 hover:text-teal-700">Impacto por Setor</a>
                        <a href="#conceitos" class="nav-link px-3 py-2 rounded-md text-sm font-medium text-stone-600 hover:text-teal-700">Conceitos-Chave</a>
                    </div>
                </div>
            </div>
        </nav>
    </header>

    <main>
        <section id="introducao" class="py-20 md:py-28">
            <div class="container mx-auto px-4 text-center">
                <p class="text-base font-semibold text-teal-600 tracking-wider uppercase">O Corpo como Capital Simbólico</p>
                <h2 class="mt-2 text-4xl md:text-5xl font-extrabold text-stone-900 tracking-tight">A Estética como Moeda no Mercado de Trabalho</h2>
                <p class="mt-6 max-w-3xl mx-auto text-lg text-stone-600">
                    Esta análise explora como a aparência física, ou "capital estético", funciona como um critério não declarado, mas poderoso, na seleção e progressão profissional. Investigamos como padrões de beleza influenciam a empregabilidade e perpetuam desigualdades, especialmente as de gênero, nas relações de trabalho contemporâneas.
                </p>
            </div>
        </section>

        <section id="criterio-velado" class="py-16 bg-white">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center">
                    <h3 class="text-3xl font-bold tracking-tight text-stone-900">O Critério Velado: Como a Estética Opera nas Sombras</h3>
                    <p class="mt-4 max-w-2xl mx-auto text-md text-stone-600">
                        A discriminação estética raramente é explícita. Ela se esconde em termos subjetivos e aparentemente neutros utilizados em processos seletivos. Explore alguns exemplos abaixo para entender como essa avaliação sutil acontece e o que ela realmente significa.
                    </p>
                </div>
                <div class="mt-12 grid gap-8 md:grid-cols-2 lg:grid-cols-3">
                    <div class="bg-stone-50 p-6 rounded-lg shadow-sm">
                        <div class="flex items-center">
                            <div class="flex-shrink-0 h-10 w-10 rounded-md bg-teal-500 flex items-center justify-center">
                                <span class="text-white font-bold text-xl">?</span>
                            </div>
                            <h4 class="ml-4 text-lg font-semibold text-stone-800">"Boa Aparência"</h4>
                        </div>
                        <p class="mt-4 text-stone-600">
                            <strong>O que parece ser:</strong> Um pedido por cuidado e profissionalismo. <br>
                            <strong>O que pode esconder:</strong> Exigência de adesão a padrões de beleza hegemônicos (jovem, magro, branco) que exclui corpos diversos e qualificados.
                        </p>
                    </div>
                    <div class="bg-stone-50 p-6 rounded-lg shadow-sm">
                        <div class="flex items-center">
                            <div class="flex-shrink-0 h-10 w-10 rounded-md bg-rose-500 flex items-center justify-center">
                                <span class="text-white font-bold text-xl">!</span>
                            </div>
                            <h4 class="ml-4 text-lg font-semibold text-stone-800">"Fit Cultural"</h4>
                        </div>
                        <p class="mt-4 text-stone-600">
                            <strong>O que parece ser:</strong> Alinhamento com os valores da empresa. <br>
                            <strong>O que pode esconder:</strong> Um filtro para contratar pessoas com aparência e estilo de vida semelhantes aos dos gestores, reforçando a falta de diversidade.
                        </p>
                    </div>
                    <div class="bg-stone-50 p-6 rounded-lg shadow-sm">
                        <div class="flex items-center">
                            <div class="flex-shrink-0 h-10 w-10 rounded-md bg-amber-500 flex items-center justify-center">
                                <span class="text-white font-bold text-xl">✓</span>
                            </div>
                            <h4 class="ml-4 text-lg font-semibold text-stone-800">"Perfil Dinâmico"</h4>
                        </div>
                        <p class="mt-4 text-stone-600">
                            <strong>O que parece ser:</strong> Busca por proatividade e energia. <br>
                            <strong>O que pode esconder:</strong> Preferência por candidatos jovens, associando juventude à capacidade de inovação e desvalorizando a experiência de profissionais mais velhos (etarismo).
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <section id="genero" class="py-16">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center">
                    <h3 class="text-3xl font-bold tracking-tight text-stone-900">A Dupla Medida: Pressões Estéticas de Gênero</h3>
                    <p class="mt-4 max-w-3xl mx-auto text-md text-stone-600">
                        As expectativas sobre a aparência no trabalho não são uniformes; elas variam drasticamente com base no gênero. Mulheres frequentemente enfrentam uma lista mais longa e rigorosa de exigências estéticas, enquanto homens são avaliados por critérios diferentes. Interaja com o gráfico para visualizar a disparidade na intensidade dessas pressões.
                    </p>
                </div>

                <div class="mt-10 text-center">
                    <div class="inline-flex rounded-md shadow-sm" role="group">
                        <button type="button" id="btnMulheres" class="btn-gender-filter active py-2 px-4 text-sm font-medium text-white bg-rose-500 rounded-l-lg hover:bg-rose-600 focus:z-10 focus:ring-2 focus:ring-rose-500">
                            Pressões sobre Mulheres
                        </button>
                        <button type="button" id="btnHomens" class="btn-gender-filter py-2 px-4 text-sm font-medium text-stone-700 bg-white rounded-r-lg border border-stone-200 hover:bg-stone-100 hover:text-teal-700 focus:z-10 focus:ring-2 focus:ring-teal-500">
                            Pressões sobre Homens
                        </button>
                    </div>
                </div>
                
                <div class="mt-8 md:grid md:grid-cols-2 md:gap-12 items-center">
                    <div class="chart-container h-96 md:h-full">
                        <canvas id="genderChart"></canvas>
                    </div>
                    <div id="gender-text-content" class="mt-8 md:mt-0">
                        <h4 id="gender-title" class="text-xl font-semibold text-rose-600">Análise: Pressões sobre Mulheres</h4>
                        <p id="gender-desc" class="mt-2 text-stone-600">
                            Para as mulheres, a avaliação estética é multifacetada, envolvendo maquiagem, peso, juventude e vestimenta de forma intensa. A expectativa de parecer "bem cuidada, mas não excessivamente", "profissional, mas feminina" cria um campo minado de julgamentos subjetivos que pode consumir tempo, dinheiro e energia mental, desviando o foco de suas competências técnicas.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <section id="setores" class="py-16 bg-white">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center">
                    <h3 class="text-3xl font-bold tracking-tight text-stone-900">Mapa da Aparência: O Peso da Estética por Setor</h3>
                    <p class="mt-4 max-w-3xl mx-auto text-md text-stone-600">
                        A importância atribuída à aparência varia significativamente entre diferentes áreas profissionais. Em setores com alta interação com o cliente, o "capital estético" é frequentemente visto como essencial, enquanto em áreas técnicas, outras competências podem ter mais peso. Selecione um setor para ver seu "perfil de pressão estética".
                    </p>
                </div>

                <div class="mt-10 text-center space-x-2 space-y-2">
                    <button class="btn-filter active px-4 py-2 text-sm font-medium bg-stone-200 text-stone-800 rounded-full" data-sector="vendas">Vendas e Atendimento</button>
                    <button class="btn-filter px-4 py-2 text-sm font-medium bg-stone-200 text-stone-800 rounded-full" data-sector="midia">Artes e Mídia</button>
                    <button class="btn-filter px-4 py-2 text-sm font-medium bg-stone-200 text-stone-800 rounded-full" data-sector="saude">Saúde</button>
                    <button class="btn-filter px-4 py-2 text-sm font-medium bg-stone-200 text-stone-800 rounded-full" data-sector="tecnologia">Tecnologia</button>
                </div>

                <div class="mt-8">
                     <div class="chart-container">
                        <canvas id="sectorChart"></canvas>
                    </div>
                </div>
            </div>
        </section>

        <section id="conceitos" class="py-16">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8 max-w-4xl">
                <div class="text-center">
                    <h3 class="text-3xl font-bold tracking-tight text-stone-900">Conceitos-Chave para Entender o Fenômeno</h3>
                    <p class="mt-4 max-w-2xl mx-auto text-md text-stone-600">
                        A discussão sobre estética e trabalho se baseia em conceitos sociológicos importantes que ajudam a nomear e analisar essas dinâmicas sociais. Expanda os tópicos abaixo para aprofundar seu conhecimento.
                    </p>
                </div>
                <div class="mt-12 space-y-4">
                    <div class="accordion-item border border-stone-200 rounded-lg bg-white">
                        <button class="accordion-header w-full flex justify-between items-center text-left p-4">
                            <span class="text-lg font-semibold text-stone-800">Capital Simbólico</span>
                            <span class="accordion-arrow text-teal-600 transform transition-transform duration-300">▼</span>
                        </button>
                        <div class="accordion-content px-4 pb-4">
                            <p class="text-stone-600">
                                Cunhado pelo sociólogo Pierre Bourdieu, é o conjunto de bens não materiais que conferem prestígio e reconhecimento social a um indivíduo, como reputação, honra e, neste contexto, a beleza. O capital estético é uma forma de capital simbólico que pode ser convertido em outras formas de capital, como o econômico (melhores salários) e o social (networking).
                            </p>
                        </div>
                    </div>
                    <div class="accordion-item border border-stone-200 rounded-lg bg-white">
                        <button class="accordion-header w-full flex justify-between items-center text-left p-4">
                            <span class="text-lg font-semibold text-stone-800">Habitus</span>
                            <button class="accordion-arrow text-teal-600 transform transition-transform duration-300">▼</button>
                        </button>
                        <div class="accordion-content px-4 pb-4">
                            <p class="text-stone-600">
                                Outro conceito de Bourdieu, o habitus refere-se a um sistema de disposições duráveis e transponíveis, uma "segunda natureza" que internalizamos através de nossas experiências sociais. Ele molda nossas percepções, gostos e comportamentos. O que consideramos "bom gosto" ou "aparência profissional" é um reflexo do habitus de uma classe ou grupo dominante, que se torna o padrão pelo qual todos são julgados.
                            </p>
                        </div>
                    </div>
                     <div class="accordion-item border border-stone-200 rounded-lg bg-white">
                        <button class="accordion-header w-full flex justify-between items-center text-left p-4">
                            <span class="text-lg font-semibold text-stone-800">Violência Simbólica</span>
                            <button class="accordion-arrow text-teal-600 transform transition-transform duration-300">▼</button>
                        </button>
                        <div class="accordion-content px-4 pb-4">
                            <p class="text-stone-600">
                               É a imposição de um sistema de símbolos e significados (como padrões de beleza) sobre um grupo social, de forma que essa imposição seja percebida como legítima e natural, até mesmo pelos dominados. A pressão para se adequar a padrões estéticos no trabalho é uma forma de violência simbólica, pois leva os indivíduos a aceitarem e reproduzirem as próprias normas que os limitam e discriminam, sem o uso de força física.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

    </main>
    
    <footer class="bg-stone-800 text-white">
        <div class="container mx-auto py-8 px-4 sm:px-6 lg:px-8 text-center">
            <p class="text-stone-300">Análise Interativa | Estética e Empregabilidade</p>
            <p class="text-sm text-stone-400 mt-2">Um projeto de visualização para conscientização sobre critérios velados nas relações de trabalho.</p>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            
            const tooltipTitle = (tooltipItems) => {
                return tooltipItems[0].label;
            };

            const tooltipLabel = (tooltipItem) => {
                return ` Nível de Pressão: ${tooltipItem.raw}`;
            };

            const formatLabel = (label) => {
                if (label.length > 16) {
                    const words = label.split(' ');
                    let currentLine = '';
                    const lines = [];
                    words.forEach(word => {
                        if ((currentLine + ' ' + word).length > 16 && currentLine.length > 0) {
                            lines.push(currentLine);
                            currentLine = word;
                        } else {
                            currentLine += (currentLine.length === 0 ? '' : ' ') + word;
                        }
                    });
                    lines.push(currentLine);
                    return lines;
                }
                return label;
            };

            const genderChartData = {
                mulheres: {
                    labels: ['Maquiagem Adequada', 'Cabelo Impecável', 'Controle do Peso', 'Aparência Jovem', 'Vestimenta Elegante'],
                    data: [8, 7, 8, 9, 7],
                    backgroundColor: 'rgba(244, 114, 182, 0.6)',
                    borderColor: 'rgba(244, 114, 182, 1)',
                    title: 'Análise: Pressões sobre Mulheres',
                    description: 'Para as mulheres, a avaliação estética é multifacetada, envolvendo maquiagem, peso, juventude e vestimenta de forma intensa. A expectativa de parecer "bem cuidada, mas não excessivamente", "profissional, mas feminina" cria um campo minado de julgamentos subjetivos que pode consumir tempo, dinheiro e energia mental, desviando o foco de suas competências técnicas.',
                    titleColor: 'text-rose-600'
                },
                homens: {
                    labels: ['Barba e Cabelo', 'Porte Físico', 'Aparência Jovem', 'Controle do Peso', 'Vestimenta de Autoridade'],
                    data: [6, 7, 5, 5, 8],
                    backgroundColor: 'rgba(20, 184, 166, 0.6)',
                    borderColor: 'rgba(20, 184, 166, 1)',
                    title: 'Análise: Pressões sobre Homens',
                    description: 'Para os homens, a pressão estética, embora geralmente menor, foca em sinais de virilidade, autoridade e dinamismo. A vestimenta (terno, relógio) é um forte marcador de status. O controle de peso e a aparência jovem também são valorizados, mas a margem para desvios do padrão costuma ser maior do que a concedida às mulheres.',
                    titleColor: 'text-teal-600'
                }
            };

            const genderCtx = document.getElementById('genderChart').getContext('2d');
            let genderChart = new Chart(genderCtx, {
                type: 'bar',
                data: {
                    labels: genderChartData.mulheres.labels,
                    datasets: [{
                        label: 'Nível de Pressão Percebida (0-10)',
                        data: genderChartData.mulheres.data,
                        backgroundColor: genderChartData.mulheres.backgroundColor,
                        borderColor: genderChartData.mulheres.borderColor,
                        borderWidth: 1
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        x: {
                            beginAtZero: true,
                            max: 10,
                            grid: { color: 'rgba(0,0,0,0.05)' }
                        },
                        y: {
                            ticks: { callback: formatLabel, autoSkip: false },
                            grid: { display: false }
                        }
                    },
                    plugins: {
                        legend: { display: false },
                        tooltip: { 
                            backgroundColor: '#292524',
                            titleFont: { size: 14, weight: 'bold' },
                            bodyFont: { size: 12 },
                            padding: 10,
                            callbacks: {
                                title: tooltipTitle,
                                label: tooltipLabel
                            }
                         }
                    }
                }
            });

            const btnMulheres = document.getElementById('btnMulheres');
            const btnHomens = document.getElementById('btnHomens');
            const genderTitle = document.getElementById('gender-title');
            const genderDesc = document.getElementById('gender-desc');

            function updateGenderChart(gender) {
                const data = genderChartData[gender];
                genderChart.data.labels = data.labels;
                genderChart.data.datasets[0].data = data.data;
                genderChart.data.datasets[0].backgroundColor = data.backgroundColor;
                genderChart.data.datasets[0].borderColor = data.borderColor;
                genderChart.update();

                genderTitle.textContent = data.title;
                genderDesc.textContent = data.description;
                genderTitle.className = `text-xl font-semibold ${data.titleColor}`;

                if (gender === 'mulheres') {
                    btnMulheres.classList.add('active', 'bg-rose-500', 'text-white');
                    btnMulheres.classList.remove('bg-white', 'text-stone-700', 'border');
                    btnHomens.classList.remove('active', 'bg-teal-500', 'text-white');
                    btnHomens.classList.add('bg-white', 'text-stone-700', 'border');
                } else {
                    btnHomens.classList.add('active', 'bg-teal-500', 'text-white');
                    btnHomens.classList.remove('bg-white', 'text-stone-700', 'border');
                    btnMulheres.classList.remove('active', 'bg-rose-500', 'text-white');
                    btnMulheres.classList.add('bg-white', 'text-stone-700', 'border');
                }
            }
            btnMulheres.addEventListener('click', () => updateGenderChart('mulheres'));
            btnHomens.addEventListener('click', () => updateGenderChart('homens'));


            const sectorChartData = {
                labels: ['Aparência Geral', 'Vestimenta Formal', 'Comunicação Não-Verbal', 'Juventude', 'Marcadores de Status'],
                vendas:   [9, 8, 9, 7, 6],
                midia:    [8, 6, 7, 9, 8],
                saude:    [7, 9, 8, 5, 4],
                tecnologia:[4, 5, 6, 6, 7],
            };
            
            const sectorCtx = document.getElementById('sectorChart').getContext('2d');
            const sectorChart = new Chart(sectorCtx, {
                type: 'radar',
                data: {
                    labels: sectorChartData.labels,
                    datasets: [{
                        label: 'Vendas e Atendimento',
                        data: sectorChartData.vendas,
                        fill: true,
                        backgroundColor: 'rgba(20, 184, 166, 0.2)',
                        borderColor: 'rgb(20, 184, 166)',
                        pointBackgroundColor: 'rgb(20, 184, 166)',
                        pointBorderColor: '#fff',
                        pointHoverBackgroundColor: '#fff',
                        pointHoverBorderColor: 'rgb(20, 184, 166)'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        r: {
                            angleLines: { color: 'rgba(0,0,0,0.1)' },
                            grid: { color: 'rgba(0,0,0,0.1)' },
                            pointLabels: { font: { size: 12 }, callback: formatLabel },
                            suggestedMin: 0,
                            suggestedMax: 10
                        }
                    },
                    plugins: {
                        legend: { position: 'top' },
                        tooltip: { 
                             backgroundColor: '#292524',
                             callbacks: {
                                label: (context) => `${context.dataset.label}: ${context.raw}`
                             }
                        }
                    }
                }
            });

            const filterButtons = document.querySelectorAll('.btn-filter');
            filterButtons.forEach(button => {
                button.addEventListener('click', () => {
                    const sector = button.dataset.sector;
                    sectorChart.data.datasets[0].data = sectorChartData[sector];
                    sectorChart.data.datasets[0].label = button.textContent;
                    sectorChart.update();

                    filterButtons.forEach(btn => btn.classList.remove('active'));
                    button.classList.add('active');
                });
            });

            const accordionItems = document.querySelectorAll('.accordion-item');
            accordionItems.forEach(item => {
                const header = item.querySelector('.accordion-header');
                header.addEventListener('click', () => {
                    const isActive = item.classList.contains('active');
                    accordionItems.forEach(i => i.classList.remove('active'));
                    if (!isActive) {
                        item.classList.add('active');
                    }
                });
            });

            const navLinks = document.querySelectorAll('.nav-link');
            const sections = document.querySelectorAll('main section');
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
            sections.forEach(section => observer.observe(section));
        });
    </script>
</body>
</html>
