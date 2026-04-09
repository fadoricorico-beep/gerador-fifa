<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gerador de Modo Carreira - FIFA</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #121212;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }
        .container {
            background-color: #1e1e1e;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            text-align: center;
            max-width: 500px;
            width: 90%;
            border: 2px solid #00df81;
        }
        h1 { color: #00df81; margin-bottom: 20px; }
        .result-box {
            text-align: left;
            background: #2a2a2a;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            display: none; /* Escondido até clicar */
        }
        .result-item { margin-bottom: 10px; border-bottom: 1px solid #3d3d3d; padding-bottom: 5px; }
        .label { font-weight: bold; color: #00df81; }
        button {
            background-color: #00df81;
            color: #121212;
            border: none;
            padding: 15px 30px;
            font-size: 18px;
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            transition: 0.3s;
            text-transform: uppercase;
        }
        button:hover { background-color: #00b368; transform: scale(1.05); }
    </style>
</head>
<body>

<div class="container">
    <h1>⚽ Career Generator</h1>
    <p>Clique abaixo para sortear as regras do seu novo desafio!</p>
    
    <button onclick="gerarCarreira()">Gerar Carreira</button>

    <div id="resultado" class="result-box">
        <div class="result-item"><span class="label">Temporadas no Clube:</span> <span id="tempo"></span></div>
        <div class="result-item"><span class="label">Escalação Obrigatória:</span> <span id="tática"></span></div>
        <div class="result-item"><span class="label">Limite de Contratações:</span> <span id="compras"></span></div>
        <div class="result-item"><span class="label">Orçamento Final:</span> <span id="dinheiro"></span></div>
        <div class="result-item"><span class="label">Objetivo da Diretoria:</span> <span id="objetivo"></span></div>
        <div class="result-item"><span class="label">Desafio de Jogador:</span> <span id="jogador"></span></div>
        <div class="result-item"><span class="label">Se falhar (Consequência):</span> <span id="punicao"></span></div>
    </div>
</div>

<script>
    const dados = {
        temporadas: ["1 Temporada", "2 Temporadas", "3 Temporadas", "Até ganhar a Champions", "5 Temporadas"],
        taticas: ["4-3-3 (Falso 9)", "3-5-2 (Jogo pelas alas)", "5-4-1 (Retranca)", "4-4-2 Clássico", "4-2-3-1 (Mentalidade ofensiva)", "3-4-3 Diamond"],
        compras: ["Máximo 1 jogador por temporada", "Máximo 3 jogadores por temporada", "Apenas jogadores da base", "Apenas jogadores da mesma nacionalidade do time", "Nenhuma contratação na primeira janela"],
        dinheiro: ["Sobrar 10% do orçamento", "Sobrar 50% do orçamento", "Gastar tudo (0 sobrando)", "Terminar com lucro de 20 milhões"],
        objetivos: ["Ganhar a Liga Nacional", "Chegar na final da Copa", "Subir de divisão (se for time pequeno)", "Ter a melhor defesa do campeonato", "Ter apenas jogadores sub-25 no elenco"],
        jogadores: ["O seu capitão deve jogar todas as partidas", "Venda o seu melhor jogador na 2ª temporada", "Transforme um lateral em ponta", "Um jogador da base deve ser o artilheiro do time", "Contrate um veterano (34+) para ser titular"],
        punicoes: ["Vender o seu titular de maior nota (Overall)", "Não pode contratar ninguém na próxima temporada", "Demitir um olheiro de 5 estrelas", "Reduzir o salário de todo o elenco (vender quem ganha mais)"]
    };

    function gerarCarreira() {
        document.getElementById('resultado').style.display = 'block';
        
        document.getElementById('tempo').innerText = sortear(dados.temporadas);
        document.getElementById('tática').innerText = sortear(dados.taticas);
        document.getElementById('compras').innerText = sortear(dados.compras);
        document.getElementById('dinheiro').innerText = sortear(dados.dinheiro);
        document.getElementById('objetivo').innerText = sortear(dados.objetivos);
        document.getElementById('jogador').innerText = sortear(dados.jogadores);
        document.getElementById('punicao').innerText = sortear(dados.punicoes);
    }

    function sortear(array) {
        return array[Math.floor(Math.random() * array.length)];
    }
</script>

</body>
</html>
