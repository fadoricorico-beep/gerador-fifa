<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ROLETA DO FC | Kauan Edition</title>
    <style>
        /* Cores e Fundo */
        :root {
            --neon-green: #00df81;
            --neon-blue: #00a2ff;
            --dark-bg: #0d0d0f;
        }

        body {
            font-family: 'Segoe UI', sans-serif;
            background-color: var(--dark-bg);
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            text-align: center;
        }

        /* Animação do Brilho do Título */
        @keyframes shine {
            to { background-position: 200% center; }
        }

        /* Estilo do Título Principal */
        .main-title {
            font-size: 4rem;
            font-weight: 900;
            text-transform: uppercase;
            font-style: italic;
            letter-spacing: -3px;
            margin: 0;
            background: linear-gradient(135deg, #fff 20%, var(--neon-green) 40%, var(--neon-blue) 60%, #fff 80%);
            background-size: 200% auto;
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: shine 3s linear infinite;
            filter: drop-shadow(0 0 10px rgba(0, 223, 129, 0.5));
        }

        /* Estilo da Etiqueta "Kauan Manager" */
        .manager-badge {
            display: inline-block;
            background: var(--neon-green);
            color: #000;
            font-weight: 800;
            padding: 5px 20px;
            border-radius: 4px;
            transform: rotate(-2deg) translateY(-10px);
            text-transform: uppercase;
            font-size: 1rem;
            box-shadow: 5px 5px 0 rgba(0,0,0,0.5);
            margin-bottom: 30px;
        }

        /* Botão */
        button {
            background: white;
            color: black;
            border: none;
            padding: 20px 50px;
            font-size: 1.2rem;
            font-weight: 900;
            border-radius: 12px;
            cursor: pointer;
            text-transform: uppercase;
            transition: 0.3s;
        }

        button:hover {
            background: var(--neon-green);
            transform: scale(1.05);
        }

        /* Caixa de Resultado */
        .result-box {
            margin-top: 30px;
            display: none;
        }

        .card {
            background: #1a1a1c;
            padding: 15px;
            margin: 10px auto;
            width: 80%;
            border-radius: 10px;
            border-left: 5px solid var(--neon-green);
            text-align: left;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1 class="main-title">ROLETA DO FC</h1>
        
        <div class="manager-badge">KAUAN MANAGER EDITION</div>

        <br>
        <button onclick="gerarCarreira()">Girar Roleta 🎲</button>

        <div id="resultado" class="result-box">
            <div class="card"><b>TIME:</b> <span id="time"></span></div>
            <div class="card"><b>OBJETIVO:</b> <span id="obj"></span></div>
        </div>
    </div>

    <script>
        const times = ["Palmeiras (A)", "Flamengo (A)", "Santos (B)", "Corinthians (A)", "São Paulo (A)"];
        const objetivos = ["Ganhar o Título", "Subir para Série A", "Vencer Clássicos"];

        function gerarCarreira() {
            document.getElementById('resultado').style.display = 'block';
            document.getElementById('time').innerText = times[Math.floor(Math.random() * times.length)];
            document.getElementById('obj').innerText = objetivos[Math.floor(Math.random() * objetivos.length)];
        }
    </script>

</body>
</html>
