# Youtube-Player

🚨 Problema com iframes do YouTube em apps híbridos (APK) — solução prática

Desde outubro de 2025, desenvolvedores começaram a enfrentar um problema com vídeos do YouTube carregados via <iframe> dentro de apps híbridos (APK) — especialmente em WebView IOS.
Até o momento, o YouTube / Google não se pronunciou oficialmente sobre a causa.
A alternativa mais estável encontrada é:
Não usar o iframe padrão do YouTube diretamente no app híbrido

Em vez disso:
Criar uma página intermediária (player.html)
O player.html:
Carrega o vídeo via API oficial
Escuta eventos do player
Envia eventos para o app com postMessage

📁 player.html (arquivo principal)
👉 Esse arquivo DEVE ser hospedado em uma URL pública (HTTPS)

Exemplo:
https://seusite.com/player.html

📁 index.html (exemplo de uso)
👉 Esse arquivo é apenas para teste local no navegador

🔄 Fluxo:

Seu app carrega um iframe/WebView
O iframe aponta para player.html
O player envia eventos via postMessage
O app escuta esses eventos

⚠️ Boas práticas

✔ Sempre usar HTTPS
✔ Validar event.origin em produção
✔ Hospedar player.html em domínio confiável

🧩 Exemplo de eventos disponíveis

Você recebe:

youtube-play
youtube-pause
youtube-ended

📌 Conclusão

Enquanto o problema do YouTube não é resolvido oficialmente, essa abordagem:

✅ Funciona em APK híbrido
✅ Evita bugs do iframe padrão
✅ Permite controle total do player
✅ É compatível com qualquer framework
