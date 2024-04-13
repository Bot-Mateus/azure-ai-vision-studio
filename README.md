# azure-ai-vision-studio-example
Demonstração de uma solução para análise de imagens construído com Azure AI Vision.

## Índice
- [Passo a passo, imagens utilizadas e resultados](#passo-a-passo-imagens-utilizadas-e-resultados)
- [Analisar imagens no Vision Studio](#analisar-imagens-no-vision-studio)
  - [Criar um recurso de serviços de IA do Azure](#criar-um-recurso-de-serviços-de-ia-do-azure)
  - [Conectar o recurso de serviços de IA do Azure ao Vision Studio](#conectar-o-recurso-de-serviços-de-ia-do-azure-ao-vision-studio)
- [Testando as Possibilidades](#testando-as-possibilidades)
  - [Detectar rostos em uma imagem](#detectar-rostos-em-uma-imagem)
    - [Teste Detecção "É Muita Gente"](#teste-detecção-é-muita-gente)
    - [Teste Detecção "Rosto Detalhado"](#teste-detecção-rosto-detalhado)
  - [Extração de texto da Imagem](#extração-de-texto-da-imagem)
    - [Teste Extração "Nota Fiscal"](#teste-extração-nota-fiscal)
    - [Teste Extração "Menu de Rua"](#teste-extração-menu-de-rua)
  - [Adicionar Descrições em imagens](#adicionar-descrições-em-imagens)
    - [Teste Descrição "Bia Mar Sol"](#teste-descrição-bia-mar-sol)
    - [Teste Descrição "Eu nas Montanhas"](#teste-descrição-eu-nas-montanhas)
  - [Identificar objetos em imagens](#identificar-objetos-em-imagens)
    - [Teste Identificação "Café dos Deuses"](#teste-identificação-café-dos-deuses)
- [IMPORTANTE: Limpeza](#importante-limpeza)
- [Como me encontrar](#como-me-encontrar)

## Passo a passo, imagens utilizadas e resultados 
[Passo a passo](https://github.com/Bot-Mateus/azure-ai-vision-studio/tree/main/passo%20a%20passo)

[Inputs](https://github.com/Bot-Mateus/azure-ai-vision-studio/tree/main/inputs)

[Outputs](https://github.com/Bot-Mateus/azure-ai-vision-studio/tree/main/outputs)

# Analisar imagens no Vision Studio

O Azure AI Vision inclui numerosas capacidades para entender o conteúdo e o contexto das imagens e extrair informações delas. O Azure AI Vision Studio permite experimentar muitas das capacidades de análise de imagem.

## Criar um recurso de serviços de IA do Azure

Você pode usar as capacidades de análise de imagem do Azure AI Vision com um recurso de serviços de IA do Azure. Se você ainda não o fez, crie um recurso de serviços de IA do Azure em sua assinatura do Azure.

1. Acesse o portal do Azure.
2. Clique em "+ Criar um recurso" e procure por "Serviços Cognitivos".
   
![Exemplo](passo%20a%20passo/1.png)

3. Selecione "Criar".
4. Configure o recurso com as configurações necessárias.

   
![Exemplo](passo%20a%20passo/2.png)

5. Após isso basta selecionar "Examinar + criar"

## Conectar o recurso de serviços de IA do Azure ao Vision Studio

Conecte o recurso de serviços de IA do Azure que você provisionou ao Vision Studio.

1. Navegue até o [Vision Studio](https://portal.vision.cognitive.azure.com).
2. Faça login e verifique se está usando o mesmo diretório em que você criou seu recurso de serviços de IA do Azure.
   Para fazer isso basta ir em "View all resources" e marcar o recurso que havia criado anteriormente.
3. Selecione o recurso que você criou como o recurso padrão.

![Exemplo](passo%20a%20passo/6.png) 

# Testando as Possibilidades

Nesta etapa eu irei mostrar os testes realizados, desde da criação até os resultados, explico um pouco sobre o JSON e dou a **minha** opnião sobre a ferramenta.
Fiquem a vontade para replicar os testes utilizando as mesmas imagens, os links estão na sessão [Passo a passo, imagens utilizadas e resultados](#passo-a-passo-imagens-utilizadas-e-resultados)

## Detectar rostos em uma imagem

Após ter feito todos esses passos está na hora de ver algo prático. Vamos começar testando a função para Detecção de Faces.

1. Acesse o Vision Studio.
2. Selecione a guia "Face" e "Detect faces in an image".

![Exemplo](passo%20a%20passo/7.png) 
   
3. Faça o upload da imagem e veja quantas faces foram encontradas.


### Teste Detecção "É Muita Gente":

![Exemplo](passo%20a%20passo/9.png) 

Nesse teste eu quis verificar se a IA daria conta de tantas faces, e fiquei satisfeito com o resultado, considerando que a imagem não está com uma resolução muito boa. 
Foram encontrados 78 rostos e se formos no arquivo JSON podemos obter informações mais detalhadas da análise:

```json
{
    "recognitionModel": "recognition_01",
    "faceRectangle": {
      "width": 30,
      "height": 39,
      "left": 794,
      "top": 291
    },
    "faceLandmarks": {
      "pupilLeft": {
        "x": 800.6,
        "y": 306.8
      },
      "pupilRight": {
        "x": 813.7,
        "y": 306.8
      },
      "noseTip": {
        "x": 805.4,
        "y": 314.2
      },
      "mouthLeft": {
        "x": 801.1,
        "y": 321.3
      },
      "mouthRight": {
        "x": 813.1,
        "y": 321.3
    },
    "faceAttributes": {
      "mask": {
        "type": "noMask",
        "noseAndMouthCovered": false
      }
    }
  },
```
Este é um pedaço do JSON gerado pela análise e contém informações sobre reconhecimento facial e atributos faciais. Vou explicar cada parte do JSON:

    "recognitionModel": "recognition_01": Este campo indica o modelo de reconhecimento facial utilizado. Neste caso, está utilizando o modelo de reconhecimento facial recognition_01.

    "faceRectangle": { "width": 30, "height": 39, "left": 794, "top": 291 }: Este objeto descreve o retângulo que contém o rosto na imagem. Ele especifica a largura, altura, posição à esquerda e posição superior do retângulo.

    "faceLandmarks": { ... }: Este objeto contém informações sobre os marcos faciais detectados na imagem, como as posições dos olhos, nariz e boca.

    "faceAttributes": { "mask": { "type": "noMask", "noseAndMouthCovered": false } }: Este objeto contém atributos faciais detectados. Neste caso, está indicando que não há máscara facial presente na pessoa detectada na imagem e que o nariz e a boca não estão cobertos.

Não inseri o JSON completo porque esse ficou muito grande, mas podem verificar ele [AQUI](https://github.com/Bot-Mateus/azure-ai-vision-studio/blob/main/outputs/muitaspessoas.json)

### Teste Detecção "Rosto Detalhado":

![Exemplo](passo%20a%20passo/10.png) 

Esse foi um teste mais "simples" e pude analisar melhor a acertividade da classificação dos atributos faciais. 
Infelizmente não é possivel ver as marcações no print, mas garanto que os pontos estavam todos corretos.

## Extração de texto da Imagem

Agora vamos analisar imagens e testar a extração de texto.

1. Acesse o Vision Studio.
2. Selecione a guia de "Optical character recognition" e "Extract text from Images".
3. Faça o upload da imagem e observe o texto extraído.

### Teste Extração "Nota Fiscal":

![Exemplo](passo%20a%20passo/12.png) 

A primeira imagem que eu testei foi uma nota fiscal e funcionou muito bem, é possivel criar automações muito legais com base no JSON gerado.

### Teste Extração "Menu de Rua":

![Exemplo](passo%20a%20passo/13.png) 

Nesse teste eu quis medir os limites dessa ferramenta usando uma imagem em baixa resolução dos famosos Menus de rua que encontramos pelo Brasil. Considerando o péssimo cenário que eu propus e que talvez nem você esteja enchergando a imagem direito, achei os resultados satisfatório.

## Adicionar Descrições em imagens

Essa função irá descrever o contéudo da imagem e para isso eu resolvi usar algumas das fotografias das minhas viagens. Vamos o que vai sair.

1. Acesse o Vision Studio.
2. Selecione a guia de "Image analysis" e "Add captions to images".
3. Faça o upload da imagem e observe a legenda gerada.

### Teste Descrição "Bia Mar Sol"

![Exemplo](passo%20a%20passo/15.png)

A descrição da imagem não é mentirosa, mesmo com desfoque e o rosto em um angulo diferente, a descrição foi satisfatória. Provavelmente podemos alcançar mais detalhes (como o por do sol) usando opções mais avançadas.

### Teste Descrição "Eu nas Montanhas"

![Exemplo](passo%20a%20passo/16.png)

Mais uma vez, uma descrição satisfatória. Considerei essa melhor que a anterior.

## Identificar objetos em imagens

A funcionalidade de detecção de objetos serve para detectar e extrair caixas delimitadoras com base em milhares de objetos e seres vivos reconhecíveis. Muito legal.

1. Selecione a opção "Detect common objects in images".
2. Faça o upload da imagem e observe os objetos detectados e suas pontuações de confiança.

### Teste Identificação "Café dos Deuses"

![Exemplo](passo%20a%20passo/19.png)

Podemos ver que foi encontrado um bom número de objetos no cenário e a acertividade também foi satisfatória. Utilizando opções mais avançadas imagino que todos os objetos poderiam ser encontrados. 

Caso queiram otimizar essas análises, fiquem a vontade para utilizar as imagens desse Laboratório.

# IMPORTANTE: Limpeza

Se você não pretende fazer mais exercícios, exclua quaisquer recursos que não precise mais para evitar custos desnecessários.

Saiba mais: [Página do Azure AI Vision](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/03-image-analysis.html)

# Como me encontrar

<p align="left">
<!-- <a href="https://elbrusagency.com/"><img src="https://img.shields.io/badge/-elbrusagency.com-3423A6?style=flat&logo=Google-Chrome&logoColor=white"/></a> -->
<a href="https://www.linkedin.com/in/mateus-carvalho-da-silva/"><img src="https://img.shields.io/badge/-Mateus%20Carvalho-0077B5?style=flat&logo=Linkedin&logoColor=white"/></a>
<a href="mailto:carvalho.silva2001@gmail.com"><img src="https://img.shields.io/badge/-carvalho.silva2001@gmail.com-D14836?style=flat&logo=Gmail&logoColor=white"/></a>
<a href="https://www.instagram.com/mateusoaksilva/"><img src="https://img.shields.io/badge/-@mateusoaksilva-E4405F?style=flat&logo=Instagram&logoColor=white"/></a>
</p>
