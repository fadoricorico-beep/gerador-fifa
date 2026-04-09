<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ROLETA DO FC | Kauan Manager</title>
    <style>
        /* CONFIGURAÇÕES DE CORES E FONTE */
        :root {
            --neon-green: #00df81;
            --neon-blue: #00a2ff;
            --dark-bg: #08080a;
            --card-bg: #121214;
            --text-color: #ffffff;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, sans-serif;
            background-color: var(--dark-bg);
            background-image: 
                radial-gradient(circle at 10% 10%, rgba(0, 223, 129, 0.05) 0%, transparent 40%),
                radial-gradient(circle at 90% 90%, rgba(0, 162, 255, 0.05) 0%, transparent 40%);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            overflow-x: hidden;
        }

        /* CONTAINER PRINCIPAL */
        .container {
            background-color: var(--card-bg);
            padding: 50px 40px;
            border-radius: 30px;
            box-shadow: 0 30px 70px rgba(0,0,0,0.9), 0 0 20px rgba(0, 223, 129, 0.1);
            text-align: center;
            max-width: 650px;
            width: 90%;
            border: 1px solid rgba(255,255,255,0.03);
            position: relative;
        }

        /* LINHA DE BRILHO NO TOPO */
        .container::before {
            content: "";
            position: absolute;
            top: 0; left: 0; right: 0; height: 3px;
            background: linear-gradient(90deg, transparent, var(--neon-green), var(--neon-blue), transparent);
            border-radius: 30px 30px 0 0;
        }

        /* ========================================= */
        /* O NOVO TÍTULO ULTRA-CHAMATIVO           */
        /* ========================================= */
        .main-title {
            margin: 0 0 10px 0;
            text-transform: uppercase;
            font-style: italic;
            letter-spacing: -3px;
            line-height: 1;
            position: relative;
            display: inline-block;
        }

        /* EFEITO DE GRADIENTE E PULSAÇÃO */
        .title-text {
            font-size: 3.8rem;
            font-weight: 900;
            background: linear-gradient(135deg, #fff 30%, var(--neon-green) 50%, var(--neon-blue) 70%, #fff 90%);
            background-size: 200% auto;
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: shine 3s linear infinite, glowPulse 2s ease-in-out infinite alternate;
            
            /* Camadas de sombra para o efeito neon */
            text-shadow: 
                0 0 10px rgba(0, 223, 129, 0.5),
                0 0 20px rgba(0, 223, 129, 0.3),
                0 0 30px rgba(0, 162, 255, 0.2);
        }

        /* ANIMAÇÃO DO GRADIENTE */
        @keyframes shine {
            to { background-position: 200% center; }
        }

        /* ANIMAÇÃO DE PULSAÇÃO DO BRILHO */
        @keyframes glowPulse {
            from { text-shadow: 0 0 10px rgba(0, 223, 129, 0.5), 0 0 20px rgba(0, 223, 129, 0.3); }
            to { text-shadow: 0 0 15px rgba(0, 223, 129, 0.7), 0 0 30px rgba(0, 162, 255, 0.5), 0 0 40px var(--neon-green); }
        }

        /* SUBTÍTULO ESTILIZADO */
        .subtitle {
            font-size: 0.9rem;
            font-weight: 700;
            color: var(--dark-bg);
            background: linear-gradient(90deg, var(--neon-green), var(--neon-blue));
            display: inline-block;
            padding: 4px 15px;
            border-radius: 6px;
            text-transform: uppercase;
            letter-spacing: 2px;
            transform: rotate(-1.5deg) translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 223, 129, 0.3);
            margin-bottom: 35px;
        }

        /* ========================================= */

        /* BOTÃO */
        button {
            background: linear-gradient(135deg, var(--neon-green), var(--neon-blue));
            color: var(--dark-bg);
            border: none;
            padding: 22px 60px;
            font-size: 1.25rem;
            font-weight: 900;
            border-radius: 16px;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-transform: uppercase;
            letter-spacing: 1px;
            box-shadow: 0 10px 25px rgba(0, 223, 129, 0.3);
        }

        button:hover {
            transform: translateY(-5px) scale(1.03);
            box-shadow: 0 15px 35px rgba(0, 223, 129, 0.5), 0 0 15px var(--neon-blue);
            background: #fff;
            color: var(--dark-bg);
        }

        button:active {
            transform: translateY(2px);
        }

        /* CAIXA DE RESULTADOS */
        .result-box {
            margin-top: 40px;
            display: none;
            animation: resultEntry 0.5s ease-out;
        }

        @keyframes resultEntry {
            from { opacity: 0; transform: translateY(20px) scale(0.95); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }

        .card {
            background: rgba(255,255,255,0.02);
            padding: 20px;
            border-radius: 16px;
            margin-bottom: 15px;
            text-align: left;
            border-left: 4px solid var(--neon-green);
            transition: 0.3s;
            position: relative;
            overflow: hidden;
        }

        .card:hover { background: rgba(255,255,255,0.05); }

        .label {
            font-size: 0.75rem;
            color: var(--neon-green);
            text-transform: uppercase;
            font-weight: 800;
            display: block;
            margin-bottom: 4px;
            letter-spacing: 1px;
        }

        .value { font-size: 1.3rem; color: #fff; font-weight: 600; }

        .badge-a { color: #ffd700; font-weight: bold; font-size: 0.8rem; text-transform: uppercase; }
        .badge-b { color: var(--neon-blue); font-weight: bold; font-size: 0.8rem; text-transform: uppercase; }

        /* RODAPÉ */
        .footer { margin-top: 30px; font-size: 0.7rem; color: #444; letter-spacing: 1px; }

    </style>
</head>
<body>

<div class="container">
    <h1 class="main-title">
        <span class="title-text">ROLETA DO FC</span>
    </h1>
    <div class="subtitle">EDITION: KAUAN MANAGER</div>
    
    <button onclick="gerarCarreira()">Girar Roleta 🎲</button>

    <div id="resultado" class="result-box">
        <div class="card"><span class="label">Time Sorteado</span><span class="value" id="time"></span></div>
        <div class="card"><span class="label">Objetivo Principal</span><span class="value" id="objetivo"></span></div>
        <div class="card"><span class="label">Mercado</span><span class="value" id="mercado"></span></div>
        <div class="card" style="border-left-color: #ff4444;"><span class="label" style="color: #ff4444;">Punição</span><span class="value" id="punicao"></span></div>
    </div>
    
    <div class="footer">VERSÃO 3.0 PRO | BRASILEIRÃO A & B</div>
</div>

<script>
    // DADOS DO SORTEIO (SEPARADOS POR SÉRIE)
    const timesA = ["Palmeiras 🏆", "Flamengo", "Atlético-MG", "Grêmio", "Botafogo 🔥", "Bragantino", "Fluminense", "Athletico-PR", "Internacional", "Fortaleza", "São Paulo", "Cuiabá", "Corinthians", "Cruzeiro", "Vasco", "Bahia", "Vitória", "Juventude", "Atlético-GO", "Criciúma"];
    const timesB = ["Santos ⚓", "Goiás", "Coritiba", "América-MG", "Novorizontino", "Mirassol", "Sport", "Vila Nova", "CRB", "Guarani", "Ceará", "Botafogo-SP", "Avaí", "Paysandu", "Ituano", "Amazonas", "Operário", "Brusque", "Chapecoense", "Ponte Preta"];
    
    const objA = ["Conquistar o Título Brasileiro", "Vaga Direta no G4", "Título do 1º Turno (Botafogo Style)", "Melhor Ataque do Campeonato", "Melhor Defesa (Muralha)", "Vencer Todos os Clássicos", "Não perder em casa", "Fazer o Artilheiro do Campeonato", "Vaga na Pré-Libertadores", "Sobreviver ao Rebaixamento"];
    const objB = ["Ser Campeão da Série B", "Garantir Acesso (G4)", "Subir com Antecedência", "Revelar um jovem de 17 anos como titular", "Ser o melhor mandante da Série B", "Vencer o clássico regional", "Não cair para a Série C", "Ter o artilheiro da Série B"];

    const mercado = ["Apenas Base", "Só Brasileiros", "Máximo 2 reforços", "Proibido comprar de rivais", "Apenas Jogadores Livres"];
    const castigos = ["Vender o melhor jogador", "Demitir o Capitão", "1 Janela sem contratar", "Vender o jogador com maior salário", "Demitir o Olheiro Principal"];

    function gerarCarreira() {
        // Exibe a caixa de resultados
        document.getElementById('resultado').style.display = 'block';
        
        // Define se o time é Série A ou B (50% de chance)
        const isSerieA = Math.random() > 0.5;
        
        if (isSerieA) {
            document.getElementById('time').innerHTML = `<span class="badge-a">[SÉRIE A]</span> ${sortear(timesA)}`;
            document.getElementById('objetivo').innerText = sortear(objA);
        } else {
            document.getElementById('time').innerHTML = `<span class="badge-b">[SÉRIE B]</span> ${sortear(timesB)}`;
            document.getElementById('objetivo').innerText = sortear(objB);
        }

        // Sorteia as outras opções
        document.getElementById('mercado').innerText = sortear(mercado);
        document.getElementById('punicao').innerText = sortear(castigos);
    }

    // Função auxiliar para sortear um item aleatório de um array
    function sortear(arr) {
        return arr[Math.floor(Math.random() * arr.length)];
    }
</script>

</body>
</html>
         
    
