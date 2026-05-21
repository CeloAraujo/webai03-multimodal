# Web AI Demo Multimodal

Projeto de demonstração web para interação com uma IA diretamente pelo navegador, agora com suporte multimodal. A aplicação permite que o usuário envie uma mensagem em texto e, opcionalmente, anexe arquivos de imagem ou áudio para serem processados junto com o prompt.

Esta versão representa uma evolução do projeto anterior, que trabalhava apenas com entrada textual. Os repositórios foram mantidos separados para facilitar a comparação entre as versões e visualizar a evolução da aplicação.

## Visão geral

O **Web AI Demo Multimodal** é uma aplicação front-end construída com HTML, CSS e JavaScript, com foco em demonstrar o uso de APIs nativas de IA no navegador.

A aplicação utiliza recursos experimentais do Google Chrome, como a **Prompt API com Gemini Nano**, para criar uma experiência local de interação com IA, sem depender diretamente de uma API externa no back-end.

A página permite:

- Enviar mensagens em texto;
- Anexar imagens;
- Anexar arquivos de áudio;
- Ajustar parâmetros de geração da IA;
- Receber respostas em tempo real por streaming;
- Cancelar uma geração em andamento;
- Verificar requisitos do navegador;
- Trabalhar com APIs nativas de IA do Chrome.

## Evolução do projeto

Este projeto foi separado em repositórios diferentes para demonstrar a evolução da aplicação.

A primeira versão do projeto tinha foco em uma interação simples com IA por texto.

Esta nova versão adiciona suporte multimodal, permitindo que a IA receba diferentes tipos de entrada:

```txt
Texto
Imagem
Áudio
```

Essa separação entre repositórios ajuda a comparar:

- A versão inicial textual;
- A nova versão multimodal;
- A evolução da arquitetura;
- A evolução da interface;
- A evolução da integração com APIs nativas de IA;
- A adição de tratamento para arquivos;
- O uso de streaming de resposta.

## Tecnologias utilizadas

- HTML5
- CSS3
- JavaScript ES Modules
- APIs nativas de IA do Chrome
- Prompt API for Gemini Nano
- LanguageModel API
- Translator API
- Language Detection API
- Google Fonts
  - DM Sans
  - DM Mono

## Estrutura esperada do projeto

Uma estrutura esperada para o projeto é:

```bash
web-ai-demo-multimodal/
├── index.html
├── style.css
├── index.js
├── AIService.js
└── README.md
```

Dependendo da organização do projeto, o serviço de IA também pode estar dentro de uma pasta específica, como:

```bash
web-ai-demo-multimodal/
├── index.html
├── style.css
├── index.js
├── services/
│   └── AIService.js
└── README.md
```

## Descrição dos arquivos

### `index.html`

Arquivo principal da aplicação. Contém a estrutura da página, incluindo:

- Importação das fontes;
- Importação do arquivo CSS;
- Cabeçalho da aplicação;
- Formulário de envio;
- Campos de configuração da IA;
- Campo de mensagem;
- Campo para anexar arquivo;
- Botões de ação;
- Área de saída da resposta;
- Importação do script JavaScript principal.

### `style.css`

Arquivo responsável pela estilização da interface.

Ele define:

- Cores globais;
- Layout principal;
- Card da aplicação;
- Campos de formulário;
- Botões;
- Área de resposta;
- Estados visuais;
- Responsividade;
- Aparência confortável para leitura.

A interface utiliza uma paleta suave, com fundo levemente bege/cinza, reduzindo o branco excessivo e melhorando o contraste dos textos.

### `index.js`

Arquivo JavaScript principal da aplicação.

Geralmente é responsável por:

- Capturar os elementos da interface;
- Ler os valores dos campos;
- Capturar a mensagem do usuário;
- Capturar o arquivo enviado;
- Chamar o serviço de IA;
- Exibir a resposta na tela;
- Atualizar a interface durante o carregamento;
- Tratar erros;
- Controlar o botão de cancelar, caso exista.

### `AIService.js`

Arquivo responsável por centralizar a integração com as APIs nativas de IA do navegador.

Ele contém a classe `AIService`, que gerencia:

- Verificação dos requisitos do navegador;
- Verificação da disponibilidade do modelo de linguagem;
- Verificação da API de tradução;
- Verificação da API de detecção de idioma;
- Criação de sessões com o modelo de IA;
- Envio de texto, imagem e áudio;
- Streaming da resposta;
- Cancelamento de requisições em andamento;
- Destruição de sessões anteriores.

## Funcionalidades

### Envio de mensagens em texto

O usuário pode digitar uma pergunta ou comando no campo de texto e enviar para a IA.

Exemplo:

```txt
Explique o que aparece nesta imagem.
```

Ou:

```txt
Resuma o conteúdo deste áudio.
```

### Suporte multimodal

A principal evolução desta versão é o suporte a entradas multimodais.

A aplicação permite enviar:

```txt
Texto
Imagem
Áudio
```

Isso significa que a IA pode receber uma pergunta em texto junto com um arquivo complementar.

Exemplos de uso:

```txt
Imagem + pergunta:
"O que está acontecendo nesta imagem?"
```

```txt
Áudio + pergunta:
"Transcreva ou resuma este áudio."
```

```txt
Texto puro:
"Explique a diferença entre aprendizado supervisionado e não supervisionado."
```

### Upload de imagem

O usuário pode anexar uma imagem para que ela seja enviada junto com a pergunta.

A aplicação identifica o tipo do arquivo usando o MIME type. Quando o arquivo é do tipo `image`, ele é convertido em um `Blob` e adicionado ao conteúdo enviado para o modelo.

Exemplos de tipos aceitos:

```txt
image/png
image/jpeg
image/webp
```

### Upload de áudio

O usuário também pode anexar arquivos de áudio.

Quando o arquivo é do tipo `audio`, ele também é convertido em `Blob` e enviado junto com a mensagem.

Exemplos de tipos possíveis:

```txt
audio/mpeg
audio/wav
audio/webm
audio/ogg
```

### Streaming de resposta

A resposta da IA é gerada por streaming.

Isso significa que o texto pode aparecer aos poucos na tela, conforme o modelo gera a resposta.

Esse comportamento melhora a experiência do usuário, porque ele não precisa esperar a resposta completa para começar a ler.

### Cancelamento de resposta

O serviço possui suporte a cancelamento usando `AbortController`.

Quando uma nova sessão é iniciada ou quando o usuário cancela a resposta, a geração anterior pode ser interrompida.

Isso evita que respostas antigas continuem sendo processadas desnecessariamente.

### Verificação de requisitos

Antes de utilizar a IA, a aplicação verifica se o navegador possui suporte aos recursos necessários.

Entre as verificações estão:

- Se o navegador é Google Chrome ou Chrome Canary;
- Se a API `LanguageModel` está disponível;
- Se a API `Translator` está disponível;
- Se a API `LanguageDetector` está disponível;
- Se o modelo de linguagem está disponível;
- Se o modelo precisa ser baixado;
- Se o dispositivo suporta o recurso.

## Requisitos

Este projeto depende de APIs experimentais do Chrome.

Por isso, é necessário usar uma versão recente do:

```txt
Google Chrome
```

ou

```txt
Google Chrome Canary
```

Além disso, algumas flags precisam estar ativadas manualmente.

## Flags necessárias no Chrome

A aplicação pode exigir a ativação das seguintes flags:

### Prompt API for Gemini Nano

Acesse no navegador:

```txt
chrome://flags/#prompt-api-for-gemini-nano
```

Ative a flag e reinicie o Chrome.

### Translation API

Acesse:

```txt
chrome://flags/#translation-api
```

Ative a flag e reinicie o Chrome.

### Language Detection API

Acesse:

```txt
chrome://flags/#language-detector-api
```

Ative a flag e reinicie o Chrome.

## Observação sobre suporte

Como as APIs utilizadas ainda são experimentais, o funcionamento pode variar conforme:

- Versão do Chrome;
- Sistema operacional;
- Disponibilidade do Gemini Nano;
- Recursos do dispositivo;
- Flags ativadas;
- Estado de download do modelo;
- Compatibilidade da máquina com IA local.

Caso o modelo ainda não esteja disponível, o navegador pode solicitar ou iniciar o download do recurso necessário.

## Funcionamento do `AIService`

A classe `AIService` é responsável por encapsular a comunicação com as APIs de IA do navegador.

Ela possui os seguintes principais métodos:

## `checkRequirements()`

Este método verifica se o ambiente do usuário está pronto para executar a IA.

Ele analisa:

- Se o navegador é baseado em Chrome;
- Se a API `LanguageModel` está disponível;
- Se a API `Translator` está disponível;
- Se a API `LanguageDetector` está disponível;
- Se o modelo está disponível;
- Se o modelo está indisponível;
- Se o modelo está baixando;
- Se o modelo pode ser baixado.

Caso exista algum problema, o método retorna uma lista de mensagens de erro para serem exibidas ao usuário.

Exemplo de possíveis mensagens:

```txt
Este recurso só funciona no Google Chrome ou Chrome Canary.
As APIs nativas de IA não estão ativas.
O modelo de linguagem de IA precisa ser baixado.
```

## `getParams()`

Este método retorna os parâmetros disponíveis do modelo de linguagem.

Ele utiliza:

```js
LanguageModel.params()
```

Esses parâmetros podem ser usados para configurar melhor os controles da interface, como valores mínimos, máximos ou padrões de `Temperature` e `Top K`.

## `createSession(question, temperature, topK, file = null)`

Este é o método principal de geração de resposta.

Ele cria uma nova sessão com o modelo de IA e recebe:

```js
question
temperature
topK
file
```

Onde:

- `question` é a mensagem digitada pelo usuário;
- `temperature` controla o nível de criatividade da resposta;
- `topK` controla a quantidade de opções consideradas pelo modelo;
- `file` é opcional e pode ser uma imagem ou áudio.

A sessão é criada com suporte aos seguintes tipos de entrada:

```js
expectedInputs: [
    { type: "text", languages: ["en"] },
    { type: "audio" },
    { type: "image" },
]
```

E com saída esperada em texto:

```js
expectedOutputs: [
    { type: "text", languages: ["en"] }
]
```

## `abort()`

Cancela a geração atual de resposta.

Esse método usa internamente um `AbortController`.

## `isAborted()`

Retorna se a geração atual foi cancelada.

## Parâmetros da IA

A aplicação possui dois parâmetros principais que influenciam a forma como a IA gera as respostas: `Temperature` e `Top K`.

Esses parâmetros não mudam a pergunta enviada pelo usuário. Eles alteram a forma como o modelo escolhe as palavras durante a geração da resposta.

Em outras palavras, a pergunta continua sendo a mesma, mas a resposta pode ficar mais objetiva, mais previsível, mais criativa ou mais variada dependendo dos valores escolhidos.

## Temperature

O parâmetro `Temperature` controla o nível de criatividade da IA.

Ele define o quanto o modelo pode variar ou “arriscar” na escolha das palavras durante a geração da resposta.

Quando a `Temperature` está baixa, a IA tende a escolher palavras mais prováveis. Isso faz com que a resposta seja mais direta, objetiva e previsível.

Quando a `Temperature` está alta, a IA passa a considerar escolhas menos óbvias. Isso pode gerar respostas mais criativas, variadas e menos previsíveis.

Exemplo simples:

```txt
Temperature baixa = resposta mais focada, direta e controlada
Temperature alta = resposta mais criativa, variada e aberta
```

Na prática:

- Use uma `Temperature` baixa para respostas técnicas, objetivas ou mais seguras;
- Use uma `Temperature` mais alta para ideias criativas, sugestões, textos mais variados ou brainstorming.

Exemplo de uso com valor baixo:

```txt
Temperature: 0.2

Resultado esperado:
Uma resposta mais direta, previsível e objetiva.
```

Exemplo de uso com valor alto:

```txt
Temperature: 0.8

Resultado esperado:
Uma resposta mais criativa, com mais variações e possibilidades.
```

Exemplo comparativo:

```txt
Pergunta:
Explique o que é inteligência artificial.

Com Temperature baixa:
Inteligência artificial é uma área da computação que cria sistemas capazes de realizar tarefas que normalmente exigiriam inteligência humana.

Com Temperature alta:
Inteligência artificial é como ensinar máquinas a perceber padrões, tomar decisões e resolver problemas de um jeito parecido com o raciocínio humano.
```

## Top K

O parâmetro `Top K` controla quantas opções de palavras a IA pode considerar ao gerar a resposta.

Durante a geração de texto, a IA calcula quais palavras têm mais chance de aparecer em seguida. O `Top K` limita essa escolha às K palavras mais prováveis.

Por exemplo, se o `Top K` estiver definido como `10`, a IA vai considerar apenas as 10 palavras mais prováveis para continuar a resposta.

Se o `Top K` estiver definido como `50`, a IA terá 50 opções possíveis para escolher a próxima palavra.

Exemplo simples:

```txt
Top K baixo = a IA escolhe entre poucas opções
Top K alto = a IA escolhe entre mais opções
```

Na prática:

- Use um `Top K` baixo para respostas mais previsíveis e controladas;
- Use um `Top K` alto para permitir mais variedade nas respostas.

Exemplo de uso com valor baixo:

```txt
Top K: 10

Resultado esperado:
A IA considera poucas opções de palavras e gera uma resposta mais limitada e previsível.
```

Exemplo de uso com valor alto:

```txt
Top K: 50

Resultado esperado:
A IA considera mais opções de palavras e pode gerar uma resposta com mais variedade.
```

Exemplo comparativo:

```txt
Frase:
O céu está...

Com Top K baixo:
O céu está azul.

Com Top K alto:
O céu está azul.
O céu está nublado.
O céu está claro.
O céu está escuro.
O céu está colorido.
```

## Diferença entre Temperature e Top K

Apesar de os dois parâmetros influenciarem a criatividade e a variação da resposta, eles funcionam de formas diferentes.

A `Temperature` controla o quanto a IA pode variar nas escolhas.

O `Top K` controla quantas opções a IA pode considerar.

Resumo simples:

```txt
Temperature = nível de criatividade
Top K = quantidade de opções disponíveis
```

Ou seja:

```txt
Temperature baixa + Top K baixo = resposta mais objetiva, segura e previsível

Temperature alta + Top K alto = resposta mais criativa, variada e menos previsível
```

Exemplo prático:

```txt
Se você quer uma resposta técnica:
Temperature: 0.2
Top K: 10

Se você quer uma resposta mais criativa:
Temperature: 0.8
Top K: 40 ou 50
```

## Fluxo de funcionamento

O fluxo básico da aplicação é:

```txt
1. O usuário abre a página.
2. A aplicação verifica se o navegador suporta as APIs necessárias.
3. O usuário digita uma mensagem.
4. O usuário ajusta Temperature e Top K.
5. Opcionalmente, o usuário anexa uma imagem ou áudio.
6. A aplicação cria uma sessão com o modelo de IA.
7. O texto e o arquivo são enviados para o modelo.
8. A IA gera uma resposta por streaming.
9. A resposta é exibida na tela.
10. A sessão pode ser cancelada ou substituída por uma nova.
```

## Exemplo de uso textual

```txt
Mensagem:
Explique a diferença entre aprendizado supervisionado e não supervisionado.

Arquivo:
Nenhum

Resultado esperado:
A IA responde usando apenas a mensagem textual como contexto.
```

## Exemplo de uso com imagem

```txt
Mensagem:
Descreva o que aparece nesta imagem.

Arquivo:
imagem.png

Resultado esperado:
A IA analisa a imagem enviada e responde em texto.
```

## Exemplo de uso com áudio

```txt
Mensagem:
Resuma o conteúdo deste áudio.

Arquivo:
audio.webm

Resultado esperado:
A IA utiliza o áudio enviado como entrada e gera uma resposta em texto.
```

## Como executar o projeto

Como o projeto é baseado em HTML, CSS e JavaScript puro, ele pode ser executado localmente no navegador.

Por utilizar módulos JavaScript e APIs experimentais do Chrome, recomenda-se executar com um servidor local.

### Opção 1: Usar Live Server no VS Code

Instale a extensão **Live Server** no VS Code.

Depois, clique com o botão direito no arquivo `index.html` e selecione:

```bash
Open with Live Server
```

Essa é a forma mais simples para testar o projeto localmente.

### Opção 2: Usar um servidor local com Node.js

Caso tenha Node.js instalado, execute:

```bash
npx serve .
```

Depois acesse a URL exibida no terminal, geralmente:

```bash
http://localhost:3000
```

### Opção 3: Usar outro servidor estático

Também é possível usar qualquer servidor estático, como:

```bash
npx http-server .
```

ou extensões semelhantes.

## Cuidados ao executar

Evite abrir o arquivo diretamente com duplo clique no `index.html`.

Como o projeto usa JavaScript Modules e APIs modernas do navegador, abrir diretamente pelo protocolo `file://` pode causar limitações.

Prefira rodar em:

```txt
http://localhost
```

ou equivalente.

## Personalização visual

As principais cores do projeto ficam centralizadas no seletor `:root` do CSS:

```css
:root {
    --bg:        #f1efe8;
    --surface:   #faf9f5;
    --border:    #d8d3c8;
    --text-1:    #141412;
    --text-2:    #4f4b43;
    --text-3:    #7c776d;
    --accent:    #245c43;
    --accent-lt: #dceee7;
    --radius:    10px;
    --shadow:    0 1px 3px rgba(0,0,0,.08), 0 6px 18px rgba(0,0,0,.06);
}
```

Essas variáveis controlam:

- Cor de fundo da página;
- Cor dos cards;
- Cor das bordas;
- Cores dos textos;
- Cor principal da interface;
- Cor de destaque;
- Sombra dos elementos;
- Arredondamento dos componentes.

## Design da interface

A interface foi pensada para ser simples, limpa e confortável para leitura.

Algumas decisões visuais:

- Fundo menos branco para reduzir cansaço visual;
- Textos com contraste mais forte;
- Cards com bordas suaves;
- Botão principal com cor de destaque;
- Uso de fonte sans-serif moderna;
- Uso de fonte monoespaçada para valores técnicos;
- Espaçamentos amplos para melhorar a leitura;
- Estrutura simples para facilitar o foco na interação com a IA.

## Responsividade

O layout utiliza uma largura máxima centralizada, permitindo boa leitura em telas maiores e menores.

Exemplo:

```css
.container {
    width: 100%;
    max-width: 620px;
}
```

Os parâmetros podem ser organizados em grid:

```css
.parameters {
    display: grid;
    grid-template-columns: 1fr 1fr;
}
```

Para telas pequenas, pode ser usado:

```css
@media (max-width: 520px) {
    .parameters {
        grid-template-columns: 1fr;
    }

    .card {
        padding: 22px;
    }

    button[type="submit"] {
        width: 100%;
        justify-content: center;
    }
}
```

## Limitações atuais

Por utilizar APIs experimentais, o projeto pode apresentar limitações.

Algumas delas são:

- Funciona apenas em versões compatíveis do Chrome ou Chrome Canary;
- Pode exigir ativação manual de flags;
- Pode depender do download do modelo local;
- O suporte multimodal pode variar conforme a versão do navegador;
- Nem todos os formatos de imagem ou áudio podem ser suportados;
- O modelo pode responder em inglês dependendo da configuração de idioma;
- O processamento depende da capacidade do dispositivo;
- As APIs podem mudar em versões futuras do Chrome.

## Possíveis melhorias futuras

Algumas melhorias que podem ser adicionadas ao projeto:

- Melhorar a interface de upload de arquivos;
- Exibir preview da imagem enviada;
- Exibir nome e tamanho do arquivo anexado;
- Adicionar botão para remover arquivo;
- Adicionar loading visual durante o processamento;
- Melhorar tratamento de erros;
- Exibir progresso de download do modelo na interface;
- Adicionar histórico de perguntas;
- Adicionar botão para limpar conversa;
- Suporte a markdown nas respostas;
- Copiar resposta para a área de transferência;
- Modo claro e modo escuro;
- Salvamento das configurações no `localStorage`;
- Validação dos parâmetros antes do envio;
- Animações suaves na exibição da resposta;
- Melhorias de acessibilidade;
- Responsividade aprimorada para telas pequenas;
- Internacionalização da interface;
- Melhor controle de idioma de entrada e saída;
- Melhor integração com a API de tradução.

## Exemplo de fluxo JavaScript esperado

Um fluxo básico no `index.js` poderia ser:

```js
import { AIService } from './AIService.js';

const aiService = new AIService();

const form = document.getElementById('question-form');
const output = document.getElementById('output');

form.addEventListener('submit', async (event) => {
    event.preventDefault();

    const formData = new FormData(form);

    const question = formData.get('question');
    const temperature = Number(formData.get('temperature'));
    const topK = Number(formData.get('topK'));
    const file = formData.get('file');

    output.textContent = '';

    try {
        const errors = await aiService.checkRequirements();

        if (errors) {
            output.textContent = errors.join('\n');
            return;
        }

        for await (const chunk of aiService.createSession(question, temperature, topK, file)) {
            output.textContent += chunk;
        }
    } catch (error) {
        output.textContent = 'Erro ao gerar resposta.';
        console.error(error);
    }
});
```

## Autor

Desenvolvido por:

```txt
Marcelo Araujo
```

Projeto voltado para estudos de Engenharia de Software com IA Aplicada.

## Licença

Este projeto pode ser utilizado para fins de estudo, prática e demonstração.

Caso seja usado em produção ou compartilhado publicamente, recomenda-se adicionar uma licença formal, como MIT, Apache 2.0 ou outra de sua preferência.
