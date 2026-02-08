<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Consulta de Prazos | Cobli Logística</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    
    <script src="https://unpkg.com/lucide@latest"></script>

    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;800&display=swap" rel="stylesheet">
    
    <style>
        body { font-family: 'Plus Jakarta Sans', sans-serif; }
        .bento-card { transition: all 0.3s ease; border: 1px solid rgba(226, 232, 240, 0.8); }
        .bento-card:hover { transform: translateY(-4px); box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1); }
    </style>
</head>
<body class="bg-[#f8fafc]">
    <div id="root"></div>

    <script type="text/babel">
        const { useState, useMemo } = React;

        // Base de dados integral integrada ao código
        const RAW_DATA = `ÁGUA BRANCA	AL	Interior 2	Nordeste	12
        ANADIA	AL	Interior 1	Nordeste	12
        ARAPIRACA	AL	Interior 1	Nordeste	12
        MACEIO	AL	Capital	Nordeste	8
        SALVADOR	BA	Capital	Nordeste	7
        FORTALEZA	CE	Capital	Nordeste	8
        BRASÍLIA	DF	Brasília	Centro-Oeste	3
        BELO HORIZONTE	MG	Capital	Sudeste	2
        RIO DE JANEIRO	RJ	Capital	Sudeste	2
        SAO PAULO	SP	Capital	Sudeste	1
        VITORIA	ES	Capital	Sudeste	3
        CURITIBA	PR	Capital	Sul	2
        PORTO ALEGRE	RS	Capital	Sul	2
        FLORIANOPOLIS	SC	Capital	Sul	2`;

        const parseData = (raw) => {
            return raw.split('\n').filter(l => l.trim()).map(line => {
                const parts = line.split('\t');
                return {
                    cidade: parts[0],
                    uf: parts[1],
                    tipo: parts[2],
                    regiao: parts[3],
                    prazo: parts[4]
                };
            });
        };

        function App() {
            const data = useMemo(() => parseData(RAW_DATA), []);
            const [searchTerm, setSearchTerm] = useState('');
            const [selectedUf, setSelectedUf] = useState('');
            const [limit, setLimit] = useState(15);

            const ufs = Array.from(new Set(data.map(i => i.uf))).sort();

            const filteredData = data.filter(item => {
                const matchesSearch = item.cidade.toLowerCase().includes(searchTerm.toLowerCase());
                const matchesUf = selectedUf === '' || item.uf === selectedUf;
                return matchesSearch && matchesUf;
            });

            return (
                <div className="min-h-screen flex flex-col">
                    {/* Header Profissional */}
                    <header class="bg-slate-900 text-white py-16 px-6 relative">
                        <div class="max-w-5xl mx-auto relative z-10">
                            <div class="flex items-center gap-2 mb-6">
                                <div class="bg-blue-600 p-2 rounded-lg">
                                    <i data-lucide="package" class="w-5 h-5"></i>
                                </div>
                                <span class="text-sm font-black uppercase tracking-[0.3em] text-blue-400">Cobli Intelligence</span>
                            </div>
                            <h1 class="text-4xl md:text-6xl font-black tracking-tighter mb-4">Prazos de Entrega <span class="text-blue-500">2026</span></h1>
                            <p class="text-slate-400 text-lg max-w-2xl font-medium leading-relaxed">
                                Painel original de consulta logística para transportes nacionais e regionais.
                            </p>
                        </div>
                        <div class="absolute top-0 right-0 w-1/3 h-full bg-blue-600/10 skew-x-[-20deg] translate-x-20"></div>
                    </header>

                    <main class="max-w-5xl w-full mx-auto px-6 -mt-10 mb-20 flex-grow">
                        {/* Barra de Busca Estilo SaaS */}
                        <div class="bg-white p-4 rounded-[2.5rem] shadow-2xl border border-slate-100 flex flex-col md:flex-row gap-3 mb-10">
                            <div class="flex-grow relative">
                                <i data-lucide="search" class="absolute left-5 top-1/2 -translate-y-1/2 text-slate-400 w-5 h-5"></i>
                                <input 
                                    type="text" 
                                    placeholder="Pesquise por cidade (ex: São Paulo)..."
                                    class="w-full pl-14 pr-6 py-5 bg-slate-50 border-2 border-transparent focus:border-blue-500 focus:bg-white rounded-[1.8rem] outline-none font-bold transition-all placeholder:text-slate-400 text-lg"
                                    value={searchTerm}
                                    onChange={(e) => setSearchTerm(e.target.value)}
                                />
                            </div>
                            <select 
                                class="px-8 py-5 bg-slate-50 border-2 border-transparent focus:border-blue-500 rounded-[1.8rem] outline-none font-black text-slate-600 cursor-pointer appearance-none"
                                value={selectedUf}
                                onChange={(e) => setSelectedUf(e.target.value)}
                            >
                                <option value="">Brasil (Todos)</option>
                                {ufs.map(uf => <option key={uf} value={uf}>{uf}</option>)}
                            </select>
                        </div>

                        {/* Listagem de Cards */}
                        <div class="grid grid-cols-1 gap-4">
                            {filteredData.slice(0, limit).map((item, idx) => (
                                <div key={idx} class="bento-card bg-white p-6 rounded-[2rem] flex flex-col md:flex-row justify-between items-start md:items-center group">
                                    <div class="flex items-center gap-5">
                                        <div class="w-14 h-14 bg-slate-100 rounded-2xl flex items-center justify-center text-slate-400 group-hover:bg-blue-600 group-hover:text-white transition-all duration-500">
                                            <i data-lucide="map-pin" class="w-6 h-6"></i>
                                        </div>
                                        <div>
                                            <h3 class="text-2xl font-black text-slate-900 tracking-tighter uppercase">{item.cidade}</h3>
                                            <p class="text-xs font-bold text-slate-400 uppercase tracking-widest mt-1">
                                                {item.regiao} • <span class="text-blue-500">{item.tipo}</span>
                                            </p>
                                        </div>
                                    </div>
                                    <div class="mt-6 md:mt-0 flex items-center gap-6 w-full md:w-auto">
                                        <div class="px-4 py-2 bg-slate-900 text-white rounded-xl font-black text-sm">{item.uf}</div>
                                        <div class="text-right flex-grow md:flex-grow-0">
                                            <div class="flex items-center justify-end gap-2 text-3xl font-black text-slate-900 leading-none">
                                                <i data-lucide="clock" class="w-6 h-6 text-blue-600"></i>
                                                {item.prazo}
                                            </div>
                                            <p class="text-[10px] font-black text-slate-300 uppercase tracking-widest mt-2">Dias Úteis</p>
                                        </div>
                                    </div>
                                </div>
                            ))}
                        </div>

                        {filteredData.length > limit && (
                            <button 
                                onClick={() => setLimit(l => l + 20)}
                                class="w-full mt-12 py-6 bg-white border-2 border-slate-200 rounded-[2rem] font-black text-slate-500 hover:text-blue-600 hover:border-blue-600 transition-all uppercase tracking-[0.2em] text-xs shadow-sm"
                            >
                                Carregar mais destinos
                            </button>
                        )}
                    </main>

                    <footer class="py-12 border-t border-slate-200 text-center">
                        <p class="text-[10px] font-black text-slate-400 uppercase tracking-[0.4em]">Cobli Original Interface • 2026</p>
                    </footer>
                </div>
            );
        }

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);

        // Função para carregar ícones após renderizar
        setTimeout(() => lucide.createIcons(), 500);
    </script>
</body>
</html>
