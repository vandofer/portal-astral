<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portal do Vando - Astral Oficial</title>
    <style>
        :root {
            --gold: #FFD700;
            --text: #ffffff;
            --glass: rgba(16, 16, 38, 0.98);
            --border: rgba(255, 215, 0, 0.3);
        }

        body {
            background: radial-gradient(circle at top, #1a1a3a 0%, #050510 100%);
            color: var(--text);
            font-family: 'Segoe UI', Tahoma, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 5px;
            margin: 0;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container { 
            width: 100%; max-width: 480px; background: var(--glass);
            padding: 12px;
            border-radius: 25px; border: 1px solid var(--border);
            box-shadow: 0 10px 40px rgba(0,0,0,0.8); box-sizing: border-box;
            backdrop-filter: blur(15px);
        }

        h1 { color: var(--gold); text-align: center; font-size: 18px; letter-spacing: 2px; margin: 5px 0 10px 0; text-shadow: 0 0 10px rgba(255, 215, 0, 0.5); }

        .vibra-box {
            background: rgba(255, 255, 255, 0.05); border-radius: 15px;
            padding: 8px;
            text-align: center; margin-bottom: 10px;
            border: 1px solid rgba(255, 215, 0, 0.1);
        }

        .circulo-cor { 
            width: 35px; height: 35px; border-radius: 50%; 
            display: inline-block; margin: 5px 0; border: 2px solid rgba(255,255,255,0.1); 
            background: transparent; transition: 0.8s; 
        }

        label { display: block; margin-bottom: 5px; color: var(--gold); font-weight: bold; font-size: 10px; text-transform: uppercase; }

        select, input {
            width: 100%; padding: 8px; margin-bottom: 8px;
            background: #000; color: white; border: 1px solid var(--gold);
            border-radius: 10px; font-size: 13px; box-sizing: border-box;
            transition: 0.3s;
        }

        select:focus, input:focus {
            outline: none;
            border-color: #fff;
            box-shadow: 0 0 8px rgba(255, 215, 0, 0.3);
        }

        .painel-botoes { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-bottom: 10px; }

        button {
            padding: 11px 5px; border-radius: 10px; border: none;
            color: white; font-weight: bold; cursor: pointer; font-size: 10px;
            text-transform: uppercase; transition: transform 0.2s, background 0.3s, box-shadow 0.3s;
            box-shadow: 0 4px 6px rgba(0,0,0,0.3);
        }

        button:active {
            transform: scale(0.96);
        }

        .btn-blue { background: linear-gradient(135deg, #1e3c72, #2a5298); }
        .btn-blue:hover { box-shadow: 0 0 10px rgba(30, 60, 114, 0.5); }

        .btn-purple { background: linear-gradient(135deg, #4b0082, #6a0dad); }
        .btn-purple:hover { box-shadow: 0 0 10px rgba(75, 0, 130, 0.5); }

        .btn-brown { background: linear-gradient(135deg, #8b4513, #a0522d); }
        .btn-brown:hover { box-shadow: 0 0 10px rgba(139, 69, 19, 0.5); }

        .btn-red { background: linear-gradient(135deg, #b22222, #dc143c); }
        .btn-red:hover { box-shadow: 0 0 10px rgba(178, 34, 34, 0.5); }

        .grade-loterias { display: grid; grid-template-columns: repeat(5, 1fr); gap: 4px; margin-top: 5px; }
        .btn-lot { background: #2f3542; font-size: 8px; padding: 8px 2px; }
        .btn-lot:hover { background: #57606f; border: 1px solid var(--gold); }

        .grade-amor { display: grid; grid-template-columns: repeat(4, 1fr); gap: 5px; }
        .btn-signo-amor {
            padding: 7px 2px; font-size: 9px; border-radius: 8px;
            border: 1px solid rgba(255, 215, 0, 0.2); background: rgba(255, 255, 255, 0.05);
            color: white; cursor: pointer; transition: 0.2s;
        }
        .btn-signo-amor:hover { background: rgba(255, 215, 0, 0.15); border-color: var(--gold); }

        #resultado {
            margin-top: 12px; padding: 12px; background: rgba(0, 0, 0, 0.5);
            border-radius: 15px; border-left: 4px solid var(--gold);
            font-size: 13px; line-height: 1.6; color: #efefef; text-align: justify;
            animation: revelarTexto 0.4s ease-out forwards;
        }

        .num-bola {
            display: inline-block; width: 28px; height: 28px; line-height: 28px;
            background: var(--gold); color: #000; border-radius: 50%;
            margin: 3px; font-weight: bold; font-size: 11px; text-align: center;
            box-shadow: 0 2px 4px rgba(0,0,0,0.3);
        }

        .footer { margin-top: 10px; font-size: 10px; color: #555; text-align: center; }

        @keyframes revelarTexto {
            from { opacity: 0; transform: translateY(6px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

    <h1>PORTAL DO VANDO ASTROS</h1>

    <div class="container">
        <div class="vibra-box" id="info-vibracao">
            <span id="nomeCor" style="font-weight: bold; font-size: 14px;">---</span><br>
            <div id="circuloCor" class="circulo-cor"></div><br>
            <span id="nomePedra" style="color: var(--gold); font-weight: bold; font-size: 11px;">AGUARDANDO...</span>
        </div>

        <label>MEU SIGNO:</label>
        <select id="signo" onchange="ativarPortal()">
            <option value="" selected disabled>Escolha seu signo...</option>
            <option value="Áries">Áries</option>
            <option value="Touro">Touro</option>
            <option value="Gêmeos">Gêmeos</option>
            <option value="Câncer">Câncer</option>
            <option value="Leão">Leão</option>
            <option value="Virgem">Virgem</option>
            <option value="Libra">Libra</option>
            <option value="Escorpião">Escorpião</option>
            <option value="Sagitário">Sagitário</option>
            <option value="Capricórnio">Capricórnio</option>
            <option value="Aquário">Aquário</option>
            <option value="Peixes">Peixes</option>
        </select>

        <div class="painel-botoes">
            <button class="btn-blue" onclick="mostrarResposta('destino')">🌟 DESTINO</button>
            <button class="btn-purple" onclick="mostrarResposta('futuro')">🚀 FUTURO</button>
            <button class="btn-brown" onclick="mostrarResposta('mensal')">📜 MENSAL</button>
            <button class="btn-red" onclick="mostrarResposta('financeiro')">💰 FINANCEIRO</button>
            
            <div style="grid-column: span 2; text-align: center; margin-top: 5px;">
                <label>GERADOR DE SORTE (Loterias)</label>
                <div class="grade-loterias">
                    <button class="btn-lot" onclick="gerarLoteria('Mega-Sena')">MEGA</button>
                    <button class="btn-lot" onclick="gerarLoteria('Dupla Sena')">DUPLA</button>
                    <button class="btn-lot" onclick="gerarLoteria('Lotofácil')">FÁCIL</button>
                    <button class="btn-lot" onclick="gerarLoteria('Lotomania')">MANIA</button>
                    <button class="btn-lot" onclick="gerarLoteria('Quina')">QUINA</button>
                </div>
            </div>
        </div>

        <div class="vibra-box" style="border-color: #ff4757; margin-bottom: 8px;">
            <label style="color:#ff4757; font-size: 9px;">💘 AFINIDADE NO AMOR</label>
            <div class="grade-amor" id="gradeAmor"></div>
        </div>

        <div id="resultado" style="min-height: 50px;">Selecione seu signo para ativar o portal.</div>

        <div class="vibra-box" style="border-color: #4b0082; margin-top: 10px;">
            <label style="color:#9b59b6">🕊️ VIDÊNCIA ESPIRITUAL DO ALÉM</label>
            <input type="text" id="meuNome" placeholder="Seu nome (Quem lê)...">
            <input type="text" id="nomeParente" placeholder="Nome de quem partiu...">
            <button class="btn-purple" onclick="realizarVidencia()">🔮 CONSULTAR VIDÊNCIA</button>
        </div>
    </div>

    <div class="footer">Portal do Vando Astros © Todos os direitos reservados</div>

    <script>
        const dadosSignos = {
            "Áries": { cor: "Vermelho", hex: "#ff4757", pedra: "Jaspe", destino: "Sua liderança abrirá caminhos inesperados hoje.", futuro: "Grandes mudanças profissionais nos próximos meses.", mensal: "Este mês exige foco na sua paciência.", financeiro: "Momento ideal para evitar gastos por impulso." },
            "Touro": { cor: "Verde", hex: "#2ed573", pedra: "Quartzo Verde", destino: "A estabilidade que você procura virá da persistência.", futuro: "Uma proposta de negócio sólida surgirá.", mensal: "Colha os frutos do que plantou nos últimos tempos.", financeiro: "Entrada de dinheiro extra prevista em breve." },
            "Gêmeos": { cor: "Amarelo", hex: "#ffa502", pedra: "Olho de Tigre", destino: "Sua comunicação resolverá um antigo mal-entendido.", futuro: "Viagens e novas conexões transformarão sua visão.", mensal: "Mês movimentado com muitas novidades sociais.", financeiro: "Analise bem novas parcerias financeiras." },
            "Câncer": { cor: "Prata", hex: "#ced6e0", pedra: "Pedra da Lua", destino: "Sua intuição está aguçada, confie no seu coração.", futuro: "Momento de harmonia e fortalecimento familiar.", mensal: "Fase de profunda renovação emocional.", financeiro: "Proteja seus bens e evite emprestar dinheiro agora." },
            "Leão": { cor: "Dourado", hex: "#ffa502", pedra: "Âmbar", destino: "Seu brilho natural atrairá uma excelente oportunidade.", futuro: "Reconhecimento merecido no seu ambiente de trabalho.", mensal: "Mês de grande poder pessoal e magnetismo.", financeiro: "Sua sorte em investimentos está em alta." },
            "Virgem": { cor: "Azul Marinho", hex: "#1e3c72", pedra: "Cianita Azul", destino: "A organização de hoje trará a paz de espírito de amanhã.", futuro: "Projetos antigos finalmente sairão do papel.", mensal: "Foco total na saúde e na rotina produtiva.", financeiro: "Economias rendendo frutos positivos." },
            "Libra": { cor: "Rosa", hex: "#ff7675", pedra: "Quartzo Rosa", destino: "O equilíbrio retornará para as suas relações.", futuro: "Novas amizades trarão alegrias duradouras.", mensal: "Período ideal para investir no seu bem-estar.", financeiro: "A estabilidade financeira será mantida com sabedoria." },
            "Escorpião": { cor: "Preto", hex: "#2f3542", pedra: "Obsidiana", destino: "Uma transformação necessária começará de dentro para fora.", futuro: "Superação definitiva de um obstáculo do passado.", mensal: "Mês de mistérios desvendados e forte poder espiritual.", financeiro: "Mudanças benéficas na sua fonte de renda." },
            "Sagitário": { cor: "Púrpura", hex: "#8e44ad", pedra: "Sodalita", destino: "Sua sede de aventura te levará a uma nova descoberta.", futuro: "Expansão de horizontes e novos conhecimentos.", mensal: "Otimismo em alta guiará suas decisões este mês.", financeiro: "Abundância batendo à sua porta, aproveite." },
            "Capricórnio": { cor: "Marrom", hex: "#747d8c", pedra: "Ônix", destino: "O trabalho duro e constante trará a vitória desejada.", futuro: "Conquista de um bem durável ou posição de destaque.", mensal: "Fase de colheita profissional e foco em metas.", financeiro: "Gerenciamento exemplar trazendo estabilidade total." },
            "Aquário": { cor: "Azul Claro", hex: "#70a1ff", pedra: "Turquesa", destino: "Suas ideias inovadoras farão a diferença ao seu redor.", futuro: "Projetos revolucionários receberão apoio.", mensal: "Mês marcado pela liberdade e originalidade.", financeiro: "Retornos financeiros vindos de fontes alternativas." },
            "Peixes": { cor: "Violeta", hex: "#a55eea", pedra: "Ametista", destino: "Conecte-se com o plano espiritual para encontrar respostas.", futuro: "Realização de um sonho antigo que parecia distante.", mensal: "Mês de forte inspiração artística e sensibilidade.", financeiro: "Siga sua intuição antes de fechar qualquer contrato." }
        };

        function ativarPortal() {
            const signo = document.getElementById("signo").value;
            if(!signo) return;
            
            const info = dadosSignos[signo];
            document.getElementById("nomeCor").innerText = info.cor;
            document.getElementById("circuloCor").style.backgroundColor = info.hex;
            document.getElementById("nomePedra").innerText = "PEDRA: " + info.pedra;
            document.getElementById("resultado").innerText = "Portal Ativado para " + signo + "! Selecione uma consulta acima.";
            
            const gradeAmor = document.getElementById("gradeAmor");
            gradeAmor.innerHTML = "";
            Object.keys(dadosSignos).forEach(s => {
                let btn = document.createElement("button");
                btn.className = "btn-signo-amor";
                btn.innerText = s.substring(0,3).toUpperCase();
                btn.onclick = () => {
                    document.getElementById("resultado").innerHTML = `<strong>Afinidade Amorosa (${signo} + ${s}):</strong> Uma combinação única com forte magnetismo e lições importantes para o crescimento mútuo.`;
                };
                gradeAmor.appendChild(btn);
            });
        }

        function mostrarResposta(tipo) {
            const signo = document.getElementById("signo").value;
            if(!signo) {
                document.getElementById("resultado").innerText = "Por favor, selecione seu signo primeiro!";
                return;
            }
            document.getElementById("resultado").innerHTML = `<strong>${tipo.toUpperCase()}:</strong> ${dadosSignos[signo][tipo]}`;
        }

        function gerarLoteria(jogo) {
            let num = [];
            let qtd = jogo === 'Mega-Sena' ? 6 : jogo === 'Dupla Sena' ? 6 : jogo === 'Lotofácil' ? 15 : jogo === 'Lotomania' ? 20 : 5;
            let max = jogo === 'Lotofácil' ? 25 : jogo === 'Lotomania' ? 99 : jogo === 'Quina' ? 80 : 60;
            
            while(num.length < qtd) {
                let n = Math.floor(Math.random() * max) + 1;
                if(!num.includes(n)) num.push(n);
            }
            num.sort((a,b) => a-b);
            
            let bolas = `<strong>Números da Sorte (${jogo}):</strong><br><br>`;
            num.forEach(n => { bolas += `<span class="num-bola">${n}</span>`; });
            document.getElementById("resultado").innerHTML = bolas;
        }

        function realizarVidencia() {
            const nome = document.getElementById("meuNome").value;
            const parente = document.getElementById("nomeParente").value;
            if(!nome || !parente) {
                document.getElementById("resultado").innerText = "Preencha ambos os nomes para receber a mensagem espiritual.";
                return;
            }
            document.getElementById("resultado").innerHTML = `<strong>Conexão Astral para ${nome}:</strong><br><br>"${nome}, aqui é ${parente}. Não pense que suas lágrimas e orações no calado da noite não foram ouvidas. Eu estou acompanhando cada passo seu. A resposta que você procura virá através de um sonho claro nos próximos dias. Continue firme, estou te guardando."`;
        }
    </script>
</body>
</html>
