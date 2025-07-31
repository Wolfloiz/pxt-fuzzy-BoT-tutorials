### @diffs true
# FuzzyBoT em Cena

## Passo 1
Neste tutorial, vamos combinar as capacidades luminosas e acústicas do FuzzyBoT para criar uma verdadeira apresentação
artística. A proposta é que ele emita sons, luzes e se movimente com uma coreografia determinada pela nossa programação. 
Para implementar, vamos criar ``||Functions:Funções||`` para tocar as notas e para piscar os LEDs, enquanto aproveitamos as funções de movimento
que já desenvolvemos anteriormente. Preparado(a)?

```template
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function frente() {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
```

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
```

## Passo 3
Para começar, acesse a aba ``||variables:Variáveis||``, e clique em **"Fazer uma variável..."**.
Vamos criar variáveis para as **sete** notas musicais: ``||variables:do||``,  ``||variables:re||``, ``||variables:mi||``,
``||variables:fa||``,  ``||variables:sol||``,  ``||variables:la||`` e  ``||variables:si||``.
Depois de nomeá-las, adicione um bloco ``||variables:definir (variável) para 0||`` para cada variável, dentro de um laço ``||basic:no iniciar||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let _do = 0
let re = 0
let mi = 0
let fa = 0
let sol = 0
let la = 0
let si = 0
```

## Passo 4
Agora, devemos definir os valores de cada uma dessas variáveis, ou seja, o valor da frequência
de cada uma dessas notas. Para isso, basta alterar os campos de **0** para os respectivos valores a seguir:

- ``||variables:do||``: 262;
- ``||variables:re||``: 294;
- ``||variables:mi||``: 330;
- ``||variables:fa||``: 349;
- ``||variables:sol||``: 392;
- ``||variables:la||``: 440; 
- ``||variables:si||``: 494

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
```

## Passo 5
Após esses blocos, acrescente ao laço ``||basic:no iniciar||`` o comando ``||music:definir volume 127||`` localizado no menu ``||music:Música||``.
Altere seu valor de **127** para **200**.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
```

## Passo 6
Agora, acesse o menu ``||rgbLed:LEDs RGB||`` e adicione o comando ``||rgbLed:Definir LEDs para LED RGB no pino P0 com 0 LEDs como RGB (GRB formato)||``
dentro do laço ``||basic:no iniciar||``. Antes de prosseguir, modifique a porta de **P0** para **P15** e a quantidade de LEDs de 
**0** para **4**.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
```

## Passo 7
Para finalizar o laço ``||basic:no iniciar||``, adicione um comando ``||basic:mostrar ícone||``, indicando que o laço foi executado
e as variáveis inicializadas.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 8
Vá ao menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada ``||Functions:piscar||``. 
Um novo laço referente à função criada é adicionado automaticamente ao código.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function piscar () {
	
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 9
Retorne ao menu ``||rgbLed:LEDs RGB||``. Ao clicar nesta aba, acesse o submenu que vai se abrir abaixo dela, com uma nova aba
denominada ``||rgbLed:...mais||``. Selecione o bloco ``||rgbLed:LEDs definir cor do pixel na posição 0 para vermelho||`` e
insira-o dentro do laço da função ``||Functions:piscar||``. 

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 10
Volte ao submenu ``||rgbLed:...mais||`` da aba ``||rgbLed:LEDs RGB||`` e insira o bloco
``||rgbLed:vermelho 0 verde 0 azul 0||`` dentro do campo **vermelho** do comando ``||rgbLed:LEDs definir cor do pixel na posição 0 para vermelho||``. 

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(0, 0, 0))
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 11
Dentro de cada **0** desse bloco, insira blocos ``||math:escolher aleatório 0 até 10||``, localizados na aba ``||math:Matemática||``.
Antes de prosseguir, altere o segundo valor de **10** para **255** em todos os casos.  
Isso vai gerar uma cor aleatória para o LED 0 sempre que essa função for executada.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 12
Duplique esse bloco três vezes e posicione os novos abaixo do original, totalizando quatro blocos idênticos.
Em seguida, altere a posição do LED de **0** em todos os blocos para **1**, **2** e **3** respectivamente.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 13
Retorne ao menu ``||rgbLed:LEDs RGB||`` e adicione o comando ``||rgbLed:LEDs mostrar||`` abaixo dos 
blocos de definição das cores para enviar o comando para acender os LEDs.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 14
Vá ao menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada ``||Functions:tocar_notas||``. Depois de nomeá-la, 
clique no botão **número** para adicionar parâmetros a essa função. Devem ser adicionados sete parâmetros com os nomes a seguir: 
``||variables:N1||``,
``||variables:N2||``,
``||variables:N3||``,
``||variables:N4||``,
``||variables:N5||``,
``||variables:N6||``,
``||variables:N7||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
	
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 15
Dentro do laço dessa nova função, adicione o bloco ``||music:play tone C médio for 1 batida until done||``, localizado 
na aba ``||music:Música||``. Clique no bloco redondo vermelho do parâmetro ``||variables:N1||`` da função para substituir
o tom ``||music:C médio||`` por ``||variables:N1||``. Modifique o próximo campo de ``||music:1 batida||`` por ``||music:1/2 batida||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 16
Retorne ao menu ``||Functions:Funções||`` e adicione os comandos ``||Functions:ligar piscar||`` e ``||Functions:ligar direita||`` nessa sequência.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 17
Em seguida, acesse a aba ``||Basic:Básico||`` para adicionar um comando de ``||Basic:pausa (ms) 100||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 18
Agora, vamos criar sequências similares aos blocos anteriores. Portanto, duplique o bloco 
``||music:play tone N1 for 1/2 batida until done||``, mas altere o parâmetro de ``||variables:N1||`` para ``||variables:N2||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 19
Em seguida, adicione os comandos ``||Functions:ligar piscar||``, ``||Functions:ligar esquerda||`` e ``||Basic:pausa (ms) 100||`` nessa sequência.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 20
Repita o processo adicionando os comandos a seguir. Lembre-se de alterar o parâmetro para ``||variables:N3||`` e o movimento para ``||Functions:direita||``.
- ``||music:play tone N3 for 1/2 batida until done||``
- ``||Functions:ligar piscar||`` 
- ``||Functions:ligar direita||`` e 
- ``||Basic:pausa (ms) 100||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 21
Seguindo a lógica, crie a sequência para o parâmetro ``||variables:N4||`` e o movimento para ``||Functions:esquerda||``.
- ``||music:play tone N4 for 1/2 batida until done||``
- ``||Functions:ligar piscar||`` 
- ``||Functions:ligar esquerda||`` e 
- ``||Basic:pausa (ms) 100||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N4, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 22
Mantenha o padrão criando a sequência para o parâmetro ``||variables:N5||`` e o movimento para ``||Functions:frente||``.
- ``||music:play tone N5 for 1/2 batida until done||``
- ``||Functions:ligar piscar||`` 
- ``||Functions:ligar frente||`` e 
- ``||Basic:pausa (ms) 100||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N4, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N5, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 23
Para o penúltimo parâmetro, ``||variables:N6||``, temos o movimento para ``||Functions:trás||``, tornando:
- ``||music:play tone N6 for 1/2 batida until done||``
- ``||Functions:ligar piscar||`` 
- ``||Functions:ligar tras||`` e 
- ``||Basic:pausa (ms) 100||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N4, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N5, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
    music.play(music.tonePlayable(N6, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    tras()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 24
No último caso, temos o parâmetro ``||variables:N7||`` e o movimento para ``||Functions:frente||``, resultando em:
- ``||music:play tone N7 for 1/2 batida until done||``
- ``||Functions:ligar piscar||`` 
- ``||Functions:ligar tras||`` e 
- ``||Basic:pausa (ms) 100||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N4, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N5, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
    music.play(music.tonePlayable(N6, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    tras()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
```

## Passo 25
Acesse a aba ``||basic:Básico||`` e adicione o laço ``||basic:sempre||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N4, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N5, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
    music.play(music.tonePlayable(N6, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    tras()
    basic.pause(100)
    music.play(music.tonePlayable(N7, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
	
})
```

## Passo 26
Em seguida, clique em ``||Advanced:Avançado||``, no menu ``||Functions:Funções||``, e insira
o comando ``||Functions:ligar tocar_notas 1 1 1 1 1 1 1||``. Dentro dos campos dos parâmetros, altere os valores **1** para a seguinte
sequência de notas (localizadas em ``||variables:Variáveis||``):
-  ``||variables:do||``
-  ``||variables:do||``
-  ``||variables:sol||``
-  ``||variables:sol||``
-  ``||variables:la||``
-  ``||variables:la||``
-  ``||variables:sol||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N4, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N5, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
    music.play(music.tonePlayable(N6, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    tras()
    basic.pause(100)
    music.play(music.tonePlayable(N7, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    tocar_notas(_do, _do, sol, sol, la, la, sol)
})
```

## Passo 27
Depois desse bloco, adicione uma ``||basic:pausa (ms)||`` de **600ms**.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N4, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N5, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
    music.play(music.tonePlayable(N6, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    tras()
    basic.pause(100)
    music.play(music.tonePlayable(N7, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    tocar_notas(_do, _do, sol, sol, la, la, sol)
    basic.pause(600)
})
```

## Passo 28
Duplique o comando ``||Functions:ligar tocar_notas||`` e altere os parâmetros para a seguinte
sequência de notas (localizadas em ``||variables:Variáveis||``):
-  ``||variables:fa||``
-  ``||variables:fa||``
-  ``||variables:mi||``
-  ``||variables:mi||``
-  ``||variables:re||``
-  ``||variables:re||``
-  ``||variables:do||``.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N4, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N5, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
    music.play(music.tonePlayable(N6, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    tras()
    basic.pause(100)
    music.play(music.tonePlayable(N7, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    tocar_notas(_do, _do, sol, sol, la, la, sol)
    basic.pause(600)
    tocar_notas(fa, fa, mi, mi, re, re, _do)
})
```

## Passo 29
Finalize com outra ``||basic:pausa (ms)||`` de **600ms**.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N4, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N5, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
    music.play(music.tonePlayable(N6, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    tras()
    basic.pause(100)
    music.play(music.tonePlayable(N7, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    tocar_notas(_do, _do, sol, sol, la, la, sol)
    basic.pause(600)
    tocar_notas(fa, fa, mi, mi, re, re, _do)
    basic.pause(600)
})
```


## Passo 30
Agora seu código está pronto! Baixe-o para o micro:bit e assista à apresentação do FuzzyBoT!
Esse projeto foi pensado para que você possa personalizar suas apresentações alterando as sequências de notas,
movimentos e cores. Utilize sua imaginação e edite suas funções para explorar novas possibilidades artísticas.


```blocks
```

## Passo 31
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function tocar_notas (N1: number, N2: number, N3: number, N4: number, N5: number, N6: number, N7: number) {
    music.play(music.tonePlayable(N1, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N2, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N3, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    direita()
    basic.pause(100)
    music.play(music.tonePlayable(N4, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    esquerda()
    basic.pause(100)
    music.play(music.tonePlayable(N5, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
    music.play(music.tonePlayable(N6, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    tras()
    basic.pause(100)
    music.play(music.tonePlayable(N7, music.beat(BeatFraction.Half)), music.PlaybackMode.UntilDone)
    piscar()
    frente()
    basic.pause(100)
}
function piscar () {
    LEDs.setPixelColor(0, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(1, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(2, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.setPixelColor(3, rgbLed.rgb(randint(0, 255), randint(0, 255), randint(0, 255)))
    LEDs.show()
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
let LEDs: rgbLed.Strip = null
let _do = 262
let re = 294
let mi = 330
let fa = 349
let sol = 392
let la = 440
let si = 494
music.setVolume(200)
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.showIcon(IconNames.Heart)
basic.forever(function () {
    tocar_notas(_do, _do, sol, sol, la, la, sol)
    basic.pause(600)
    tocar_notas(fa, fa, mi, mi, re, re, _do)
    basic.pause(600)
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
