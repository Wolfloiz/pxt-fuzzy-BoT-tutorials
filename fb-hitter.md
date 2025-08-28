### @diffs true
# Rebatedor

## Passo 1
Neste projeto, vamos conhecer a câmera do FuzzyBoT! Ela funciona como um sensor de visão computacional inteligente,
servindo como verdadeiros olhos para permitir que o robô "visualize" o ambiente. Especificamente nessa atividade, 
vamos programar para que ela identifique uma esfera amarela e acione o servomotor para rebatê-la como um 
jogador de ping-pong.

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||basic:Básico||`` e adicione um bloco ``||basic:pausa (ms) 100||`` no laço ``||basic:no iniciar||``.
Modifique a duração da pausa de **100ms** para **2000ms** (2 segundos).

```blocks
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 4
Vá ao menu ``||Advanced:Avançado||``, acesse ``||Camera:Sensor Câmera||`` e selecione o bloco
``||Camera:Inicializar câmera - Porta I2C - Endereço 0x60||``. Posicione o bloco abaixo
da ``||basic:pausa||``. 

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
basic.forever(function () {
	
})
```

## Passo 5
Retorne à categoria ``||Camera:Sensor Câmera||`` e adicione o bloco ``||Camera:Habilitar modo Cor||`` 
no laço ``||basic:no iniciar||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
basic.forever(function () {
	
})
```

## Passo 6
Feito isso, acesse a aba ``||rgbLed:LEDs RGB||`` e insira o bloco ``||rgbLed:definir LEDs para LED RGB no pino P0 com 0 LEDs como RGB (GRB formato)||``.
Antes de prosseguir, altere a porta de ``||rgbLed:P0||`` para ``||rgbLed:P15||`` e o número de LEDs de **0** para **4**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
	
})
```

## Passo 7
Acesse a aba ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Crie uma variável denominada: ``||variables:PingPong||``.
Depois de nomeá-la, adicione um bloco ``||variables:definir PingPong para 0||`` dentro deste ``||basic:no iniciar||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
basic.forever(function () {
	
})
```

## Passo 8
Feito isso, acesse o menu ``||fuzzyBot:FuzzyBoT||`` e adicione o comando ``||fuzzyBot:servo S1 definir para ângulo 0||``
no laço ``||basic:no iniciar||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.forever(function () {
	
})
```

## Passo 9
Retorne à categoria ``||basic:Básico||`` e adicione uma ``||basic:pausa (ms) 1000||`` de **1 segundo** e o comando ``||basic:mostrar ícone||`` para finalizar o laço ``||basic:no iniciar||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
	
})
```

## Passo 10
Agora, vamos passar para a programação do loop ``||basic:sempre||``.
Acesse a categoria ``||logic:Lógica||`` e adicione o laço ``||logic:se então||``.
Ainda nesse menu, use o bloco comparador ``||logic:0 < 0||`` dentro do campo **verdadeiro** desse laço.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (0 < 0) {
    	
    }
})
```

## Passo 11
Modifique o sinal do comparador de **<** para **>**. Em seguida, volte à aba do ``||Camera:Sensor Câmera||``,
na seção de operações, e use o bloco verde de bordas arredondadas ``||Camera:Resultados detectados no modo Cor||``
no primeiro campo do comparador, substituindo o valor **0**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
    	
    }
})
```

## Passo 12
Dentro do ``||logic:então||``, insira um novo laço ``||logic:se então||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (true) {
        	
        }
    }
})
```

## Passo 13
Volte à categoria do ``||Camera:Sensor Câmera||``,
na seção de operações, e use o bloco verde de bordas triangulares ``||Camera:Cor preto reconhecida da configuração 1||``
para substituir o **verdadeiro** deste novo laço ``||logic:se então||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorBlack, 1)) {
        	
        }
    }
})
```

## Passo 14
Clique na seta desse bloco para alterar de cor **preta** para **amarelo**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
        	
        }
    }
})
```

## Passo 15
Dentro do ``||logic:então||`` desse laço, adicione o bloco ``||variables:definir PingPong para 0||``.
Altere o valor da variável de **0** para **1**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
        	PingPong = 1
        }
    }
})
```

## Passo 16
Volte ao menu do ``||Camera:Sensor Câmera||`` e acrescente o comando ``||Camera:Habilitar modo Cor||`` dentro 
do ``||logic:então||``. Clique na seta para alterar de **habilitar** para **desabilitar**.  

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
            PingPong = 1
            Camera.VisionSetStatus(sengo2_status.Disable, sengo_vision_e.kVisionColor)
        }
    }
})
```

## Passo 17
Feito isso, acrescente outro laço ``||logic:se então senão||`` dentro de ``||basic:sempre||``, abaixo dos anteriores (não dentro).
Aproveite para adicionar um bloco comparador ``||logic:0 = 0||`` no campo **verdadeiro**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
            PingPong = 1
            Camera.VisionSetStatus(sengo2_status.Disable, sengo_vision_e.kVisionColor)
        }
    }
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Passo 18
Dentro do primeiro campo desse comparador, insira a variável ``||variables: PingPong||``.
Já no segundo campo, altere o valor de **0** para **1**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
            PingPong = 1
            Camera.VisionSetStatus(sengo2_status.Disable, sengo_vision_e.kVisionColor)
        }
    }
    if (PingPong == 1) {
    	
    } else {
    	
    }
})
```

## Passo 19
Dentro do ``||logic:então||``, adicione o bloco ``||basic:mostrar ícone||`` e altere o símbolo para 
o losango (diamante). Em seguida, acesse a categoria ``||rgbLed:LEDs RGB||`` e insira o bloco     
``||rgbLed:LEDs mostrar cor vermelho||``. Clique na seta e altere para ``||rgbLed:amarelo||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
            PingPong = 1
            Camera.VisionSetStatus(sengo2_status.Disable, sengo_vision_e.kVisionColor)
        }
    }
    if (PingPong == 1) {
        basic.showIcon(IconNames.Diamond)
        LEDs.showColor(rgbLed.colors(NeoPixelColors.Yellow))
    } else {
    	
    }
})
```

## Passo 20
Retorne à aba ``||basic:Básico||`` e adicione um bloco ``||basic:pausa (ms)||`` de **1000ms** (1 segundo).
Depois desse comando, acrescente um ``||fuzzyBot:servo S1 definir para ângulo 0||`` localizado na categoria
``||fuzzyBot:FuzzyBoT||``. Altere o valor do ângulo de **0** para **180**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
            PingPong = 1
            Camera.VisionSetStatus(sengo2_status.Disable, sengo_vision_e.kVisionColor)
        }
    }
    if (PingPong == 1) {
        basic.showIcon(IconNames.Diamond)
        LEDs.showColor(rgbLed.colors(NeoPixelColors.Yellow))
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 180)
    } else {
    	
    }
})
```

## Passo 21
Duplique os dois últimos blocos: a ``||basic:pausa (ms)||`` e o ``||fuzzyBot:servo S1 definir para ângulo 180||``.
Posicione os novos blocos logo abaixo dos antigos, alterando o valor do ângulo de **180** para **0**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
            PingPong = 1
            Camera.VisionSetStatus(sengo2_status.Disable, sengo_vision_e.kVisionColor)
        }
    }
    if (PingPong == 1) {
        basic.showIcon(IconNames.Diamond)
        LEDs.showColor(rgbLed.colors(NeoPixelColors.Yellow))
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 180)
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
    } else {
    	
    }
})
```

## Passo 22
Agora, dentro do ``||logic:senão||``, insira o comando ``||Camera:Habilitar modo Cor||``, encontrado
na categoria ``||Camera:Sensor Camera||``. 

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
            PingPong = 1
            Camera.VisionSetStatus(sengo2_status.Disable, sengo_vision_e.kVisionColor)
        }
    }
    if (PingPong == 1) {
        basic.showIcon(IconNames.Diamond)
        LEDs.showColor(rgbLed.colors(NeoPixelColors.Yellow))
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 180)
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
    } else {
        Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
    }
})
```

## Passo 23
Adicione uma ``||basic:pausa (ms)||`` de **1000ms** (1 segundo). Feito isso, acesse a categoria
``||rgbLed:LEDs RGB||`` e adicione o bloco ``||rgbLed:LEDs limpar||``, seguido do comando 
``||rgbLed:LEDs mostrar||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
            PingPong = 1
            Camera.VisionSetStatus(sengo2_status.Disable, sengo_vision_e.kVisionColor)
        }
    }
    if (PingPong == 1) {
        basic.showIcon(IconNames.Diamond)
        LEDs.showColor(rgbLed.colors(NeoPixelColors.Yellow))
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 180)
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
    } else {
        Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
        basic.pause(1000)
        LEDs.clear()
        LEDs.show()
    }
})
```

## Passo 24
Finalize esse ``||logic:senão||`` com um comando de ``||basic:mostrar ícone||``. 

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
            PingPong = 1
            Camera.VisionSetStatus(sengo2_status.Disable, sengo_vision_e.kVisionColor)
        }
    }
    if (PingPong == 1) {
        basic.showIcon(IconNames.Diamond)
        LEDs.showColor(rgbLed.colors(NeoPixelColors.Yellow))
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 180)
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
    } else {
        Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
        basic.pause(1000)
        LEDs.clear()
        LEDs.show()
        basic.showIcon(IconNames.Heart)
    }
})
```

## Passo 25
Transfira seu código para o micro:bit, construa a estrutura e verifique se o FuzzyBoT está
identificando a esfera amarela e acionando o servo para rebatê-la.

```blocks
```

## Passo 26
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
let PingPong = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
basic.pause(1000)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    if (Camera.Detected(sengo_vision_e.kVisionColor) > 0) {
        if (Camera.DetectedColor(color_label_e.kColorYellow, 1)) {
            PingPong = 1
            Camera.VisionSetStatus(sengo2_status.Disable, sengo_vision_e.kVisionColor)
        }
    }
    if (PingPong == 1) {
        basic.showIcon(IconNames.Diamond)
        LEDs.showColor(rgbLed.colors(NeoPixelColors.Yellow))
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 180)
        basic.pause(1000)
        fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
    } else {
        Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionColor)
        basic.pause(1000)
        LEDs.clear()
        LEDs.show()
        basic.showIcon(IconNames.Heart)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
