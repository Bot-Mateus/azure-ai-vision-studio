# azure-ai-vision-studio-example
Demonstração de uma solução para análise de imagens construído com Azure AI Vision.

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

# Testando as Possibilidade

## Detectar rostos em uma imagem

Após ter feito todos esses passos está na hora de ver algo prático. Vamos começar testando a função para Detecção de Faces.

1. Acesse o Vision Studio.
2. Selecione a guia "Face" e "Detect faces in an image".

![Exemplo](passo%20a%20passo/7.png) 
   
3. Faça o upload da imagem e veja quantas faces foram encontradas.

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

Não inseri o JSON completo porque esse ficou muito grande, mas podem verificar ele (AQUI)[]
## Gerar legendas para uma imagem

Agora você está pronto para usar o Vision Studio para analisar imagens tiradas por uma câmera na loja Northwind Traders.

1. Acesse o Vision Studio.
2. Selecione a guia de análise de imagem e adicione legendas às imagens.
3. Faça o upload da imagem e observe a legenda gerada.

## Identificar objetos em imagens

Use a funcionalidade de detecção de objetos para detectar e extrair caixas delimitadoras com base em milhares de objetos e seres vivos reconhecíveis.

1. Selecione a opção de detectar objetos comuns em imagens.
2. Faça o upload da imagem e observe os objetos detectados e suas pontuações de confiança.

## Limpeza

Se você não pretende fazer mais exercícios, exclua quaisquer recursos que não precise mais para evitar custos desnecessários.

Saiba mais: [Página do Azure AI Vision](link-para-a-página)
