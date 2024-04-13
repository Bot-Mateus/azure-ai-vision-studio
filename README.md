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
      "eyebrowLeftOuter": {
        "x": 797,
        "y": 303.8
      },
      "eyebrowLeftInner": {
        "x": 803.6,
        "y": 303.4
      },
      "eyeLeftOuter": {
        "x": 798.5,
        "y": 306.9
      },
      "eyeLeftTop": {
        "x": 800.8,
        "y": 306.3
      },
      "eyeLeftBottom": {
        "x": 800.3,
        "y": 307.3
      },
      "eyeLeftInner": {
        "x": 802.9,
        "y": 306.9
      },
      "eyebrowRightInner": {
        "x": 809.4,
        "y": 303.4
      },
      "eyebrowRightOuter": {
        "x": 818.1,
        "y": 304.5
      },
      "eyeRightInner": {
        "x": 811.4,
        "y": 306.8
      },
      "eyeRightTop": {
        "x": 813.5,
        "y": 306.2
      },
      "eyeRightBottom": {
        "x": 813.8,
        "y": 307.3
      },
      "eyeRightOuter": {
        "x": 816.2,
        "y": 306.8
      },
      "noseRootLeft": {
        "x": 804.7,
        "y": 307.3
      },
      "noseRootRight": {
        "x": 808.4,
        "y": 307.2
      },
      "noseLeftAlarTop": {
        "x": 803,
        "y": 312.2
      },
      "noseRightAlarTop": {
        "x": 809.7,
        "y": 312.1
      },
      "noseLeftAlarOutTip": {
        "x": 802,
        "y": 315
      },
      "noseRightAlarOutTip": {
        "x": 811.1,
        "y": 315.1
      },
      "upperLipTop": {
        "x": 806.6,
        "y": 320.6
      },
      "upperLipBottom": {
        "x": 806.3,
        "y": 321.4
      },
      "underLipTop": {
        "x": 806.3,
        "y": 322.1
      },
      "underLipBottom": {
        "x": 806.3,
        "y": 323.3
      }
    },
    "faceAttributes": {
      "mask": {
        "type": "noMask",
        "noseAndMouthCovered": false
      }
    }
  },
```

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
