# Achou-que-eu-ia-esquecer
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aniversário Especial</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin: 0;
            overflow: hidden;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(270deg, #ff758c, #ff7eb3, #ffdf7e);
            background-size: 600% 600%;
            animation: backgroundAnimation 10s ease infinite;
        }
        @keyframes backgroundAnimation {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        .container {
            position: absolute;
            width: 500px;
            height: 400px;
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            opacity: 1;
            transition: opacity 0.5s ease-in-out;
        }
        .hidden {
            opacity: 0;
            pointer-events: none;
        }
        .fireworks {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            pointer-events: none;
            transition: opacity 1s;
        }
        .sparkle {
            position: absolute;
            width: 5px;
            height: 5px;
            background: yellow;
            border-radius: 50%;
            animation: sparkle 1s linear infinite;
        }
        @keyframes sparkle {
            0% { transform: scale(1); opacity: 1; }
            100% { transform: scale(4); opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="container" id="telaInicial">
        <h2>Olha só quem tá fazendo aniversário hoje 😱</h2>
        <p>Essa é fácil pra você, data da primeira vez que saímos juntos para o bombar? 🤔</p>
        <input type="password" id="senha" placeholder="DD/MM/AAAA">
        <button onclick="verificarSenha()">Entrar</button>
    </div>

    <div class="container hidden" id="telaMensagem">
        <h2>Visando sua saúde mental e a minha...</h2>
        <p>Essa foi a forma que encontrei de te prestigiar nessa data tão especial sem precisar te desbloquear de tudo heheh 🥳</p>
        <button onclick="mostrarCarta()">🎂</button>
    </div>

    <div class="container hidden" id="telaCarta">
        <p>Hoje é um dia especial, e, mesmo com tudo o que aconteceu, eu queria te lembrar o quanto você significa pra mim.</p>
        <p>Que você tenha um ano cheio de alegrias, conquistas e, acima de tudo, felicidade. Eu sempre vou guardar com carinho os momentos que passamos juntos.</p>
        <p>Com todo o meu afeto e gratidão por tudo o que vivemos. ❤️</p>
        <button onclick="mostrarResposta()">Resposta</button>
    </div>

    <div class="container hidden" id="telaResposta">
        <h3>Agora é a sua vez de me responder!</h3>
        <textarea id="resposta" placeholder="Digite sua resposta aqui..." rows="4" cols="40"></textarea>
        <button onclick="finalizarResposta()">Finalizar</button>
    </div>

    <div class="fireworks" id="fogos"></div>

    <script>
        function verificarSenha() {
            let senhaCorreta = "16/03/2024"; 
            let senhaDigitada = document.getElementById("senha").value;
            if (senhaDigitada === senhaCorreta) {
                transicao("telaInicial", "telaMensagem");
            } else {
                alert("Senha incorreta! Tente novamente.");
            }
        }

        function mostrarCarta() {
            transicao("telaMensagem", "telaCarta");
        }

        function mostrarResposta() {
            transicao("telaCarta", "telaResposta");
        }

        function finalizarResposta() {
            let resposta = document.getElementById("resposta").value;
            if (resposta.trim() === "") {
                alert("Por favor, escreva uma resposta.");
            } else {
                transicao("telaResposta", "fogos");
                iniciarFogos();
            }
        }

        function transicao(esconder, mostrar) {
            document.getElementById(esconder).classList.add("hidden");
            setTimeout(() => {
                document.getElementById(mostrar).classList.remove("hidden");
            }, 500);
        }

        function iniciarFogos() {
            let fogos = document.getElementById("fogos");
            fogos.style.opacity = "1";
            fogos.style.pointerEvents = "auto";
            for (let i = 0; i < 50; i++) {
                let spark = document.createElement("div");
                spark.classList.add("sparkle");
                document.body.appendChild(spark);
                spark.style.left = Math.random() * window.innerWidth + "px";
                spark.style.top = Math.random() * window.innerHeight + "px";
                setTimeout(() => spark.remove(), 1000);
            }
        }
    </script>
</body>
</html>
