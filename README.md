
# Discord Informer

Automação em Python para monitorar e enviar automaticamente para um canal do Discord via webhook.

---

## 📌 Objetivo

Automatizar a verificação de novos informativos no site oficial da SAE Brasil e enviar alertas ao Discord sempre que houver novidades.
Entretanto, o projeto é facilmente generalizável para web scraping de qualquer página.
---
## Funcionamento ⚙️

Utiliza-se um script que vasculha a página escolhida pelo elemento HTML de interesse com a biblioteca Requests e BeautifulSoup4, tratando os dados recebidos através de manipulação de arquivos JSON em três etapas. 

Primeiramente, guardamos o conteúdo HTML recebido e processado em um dicionário python e carregado para uma string JSON, tido como as atualizações. Após, comparam-se as atualizações com um arquivo JSON já inicializado com os informativos prévios. Na primeira instanciação do código, esse arquivo é inicialmente vazio.

Caso os arquivos sejam idênticos, o processo entende que não houveram novas entradas desde a última verificação. A inicialização do processo e o resultado da verificação é registrada em um arquivo log. 

Havendo diferença entre os arquivos, o conteúdo dos informativos prévios é sobrescrito. Formatam-se os dados para uma mensagem facilmente legível.

Com a mensagem pronta, acessa-se o webhook com a biblioteca discord-webhook, e é enviado um alerta ao canal especificado na url que, para prevenir ataques ao servidor, é guardada em variável de ambiente, acessada via bilbioteca OS e DOTENV.

