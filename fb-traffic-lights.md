### @diffs true
# Semáforo

## Passo 1
Neste tutorial, vamos aprender a acionar os LEDs RGB que ficam na parte inferior do chassi do 
FuzzyBoT. Eles são tratados como um vetor (sequência) de LEDs que podemos controlar as cores, brilhos e 
forma de acender através dos comandos na aba ``||rgbLed:LEDs RGB||``.

```template
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
```

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
```

## Passo 3
Acesse a aba ``||basic:Básico||`` e adicione o laço ``||basic:no iniciar||`` ao seu código.
Em seguida, acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Crie uma variável chamada: ``||variables:velocidade||``. 
Por fim, adicione o bloco ``||variables:definir velocidade para 0||`` que
aparecerá ao criá-la para dentro do laço ``||basic:no iniciar||``.  

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let iniciar = 0
let velocidade = 0
```

## Passo 4
Agora, acesse o menu ``||rgbLed:LEDs RGB||`` e adicione o comando ``||rgbLed:Definir LEDs para LED RGB no pino P0 com 0 LEDs como RGB (GRB format)||``
dentro do laço ``||basic:no iniciar||``. Antes de prosseguir, modifique a porta de **P0** para **P15** e a quantidade de LEDs de 
**0** para **4**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let iniciar = 0
let velocidade = 0
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
```

## Passo 5
Feito isso, prosseguimos para a criação das  ``||Functions:Funções||``.
Então, clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada ``||Functions:sinal_vermelho||``. 
Um novo laço referente à função criada é adicionado automaticamente ao código.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
	
}
let iniciar = 0
let velocidade = 0
let LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
```

## Passo 6
Retorne ao menu ``||rgbLed:LEDs RGB||``. Ao clicar nesta aba, acesse o submenu que vai se abrir abaixo dela, com uma nova aba
denominada ``||rgbLed:...mais||``. Selecione o bloco ``||rgbLed:LEDs definir cor do pixel na posição 0 para vermelho||`` e
insira-o dentro do laço da função ``||Functions:sinal_vermelho||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
```

## Passo 7
Duplique esse bloco três vezes e posicione os novos abaixo do original, totalizando quatro blocos idênticos.
Em seguida, altere a posição do LED de **0** em todos os blocos para **1**, **2** e **3** respectivamente.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
```

## Passo 8
Retorne ao menu ``||rgbLed:LEDs RGB||`` e adicione o comando ``||rgbLed:LEDs mostrar||`` abaixo dos 
blocos de definição das cores para enviar o comando para acender os LEDs.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
```

## Passo 9
Duplique o laço inteiro da função ``||Functions:sinal_vermelho||`` duas vezes, criando as novas funções 
``||Functions:sinal_amarelo||`` e ``||Functions:sinal_verde||``. Para renomeá-las, basta clicar (ou tocar) no 
campo branco onde está o nome original para abrir a digitação do novo nome.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
```

## Passo 10
Agora, altere as cores dos blocos de definição em cada laço. Ou seja, na função ``||Functions:sinal_amarelo||``, 
modifique as cores para ``||rgbLed:amarelo||``. Já na função ``||Functions:sinal_verde||``, modifique as cores para
``||rgbLed:verde||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
```

## Passo 11
Acesse a aba ``||basic:Básico||`` e adicione o laço ``||basic:sempre||`` ao seu código.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
	
})
```

## Passo 12
Feito isso, adicione um laço ``||Logic:se então senão||`` dentro do ``||basic:sempre||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 13
Volte à aba ``||Logic:Lógica||`` e adicione um bloco comparador ``||Logic:0 = 0||`` para substituir o ``||Logic:verdadeiro||``.
Acesse o menu de ``||variables:Variáveis||`` e selecione o bloco redondo da variável ``||variables:iniciar||`` para 
substituir o primeiro campo do comparador. Em seguida, altere o segundo campo de **0** para **1**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
    	
    } else {
    	
    }
})
```

## Passo 14
Agora, dentro do ``||logic:então||``, podemos combinar as ações desejadas. Para isso, comece acessando 
``||Advanced:Avançado||``, clique em ``||Functions:Funções||`` e selecione o comando ``||Functions:ligar sinal_vermelho||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
    } else {
    	
    }
})
```

## Passo 15
Retorne à aba ``||basic:Básico||`` e adicione uma ``||basic:pausa (ms)||`` após ligar essa função.
Altere a duração da ``||basic:pausa||`` de **100ms** para **3000ms**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
    } else {
    	
    }
})
```

## Passo 16
Volte à ``||Functions:Funções||`` e selecione o comando ``||Functions:ligar sinal_verde||``.
Posicione-o após o bloco de ``||basic:pausa||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
        sinal_verde()
    } else {
    	
    }
})
```

## Passo 17
Acesse o menu de ``||variables:Variáveis||`` e adicione o bloco ``||variables:definir (variável) para 0||`` 
abaixo do ``||Functions:ligar sinal_verde||``. Clique na seta para selecionar a variável ``||variables:velocidade||`` e, em seguida,
modifique o valor de **0** para **100**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
        sinal_verde()
        velocidade = 100
    } else {
    	
    }
})
```

## Passo 18
Agora, acesse a aba ``||fuzzyBot:FuzzyBoT||`` e adicione o bloco ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||`` abaixo da 
definição da variável. Clique na seta para alterar de motor ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
        sinal_verde()
        velocidade = 100
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    } else {
    	
    }
})
```

## Passo 19
Modifique o valor de velocidade desse bloco de **0** para o valor da variável ``||variables:velocidade||``, localizado
na aba de ``||variables:Variáveis||``.   

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
        sinal_verde()
        velocidade = 100
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
    } else {
    	
    }
})
```

## Passo 20
Em seguida, adicione uma ``||basic:pausa||`` de **1500ms** e o comando de ``||Functions:ligar sinal_amarelo||`` 
depois dessa pausa.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
        sinal_verde()
        velocidade = 100
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        basic.pause(1500)
        sinal_amarelo()
    } else {
    	
    }
})
```

## Passo 21
Agora, adicione outro bloco ``||variables:definir velocidade para 0||``, mas altere seu valor para **40**.
Depois disso, duplique o bloco ``||fuzzyBot:Motor todos mover para frente com a velocidade||`` ``||variables:velocidade||``, já inserido alguns blocos acima.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
        sinal_verde()
        velocidade = 100
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        basic.pause(1500)
        sinal_amarelo()
        velocidade = 40
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
    } else {
    	
    }
})
```

## Passo 22
Finalizando esse laço ``||logic:então||``, acrescente outra ``||basic:pausa||`` de **1500ms** e o comando de 
``||fuzzyBot:parar motor esquerdo||`` localizado na aba ``||fuzzyBot:FuzzyBoT||``. Clique na seta para alterar de 
motor ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
        sinal_verde()
        velocidade = 100
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        basic.pause(1500)
        sinal_amarelo()
        velocidade = 40
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        basic.pause(1500)
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
    	
    }
})
```

## Passo 23
Agora, prosseguindo para o ``||logic:senão||``, duplique o comando ``||fuzzyBot:parar motor todos||`` e posicione-o 
dentro deste novo laço. Em seguida, acesse o menu ``||rgbLed:LEDs RGB||`` adicione o bloco
``||rgbLed:LEDs limpar||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
        sinal_verde()
        velocidade = 100
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        basic.pause(1500)
        sinal_amarelo()
        velocidade = 40
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        basic.pause(1500)
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
        LEDs.clear()
    }
})
```

## Passo 24
Por fim, retorne ao menu ``||rgbLed:LEDs RGB||`` adicione o bloco
``||rgbLed:LEDs mostrar||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
        sinal_verde()
        velocidade = 100
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        basic.pause(1500)
        sinal_amarelo()
        velocidade = 40
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        basic.pause(1500)
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
        LEDs.clear()
        LEDs.show()
    }
})
```

## Passo 25
Transfira seu código para o micro:bit e teste se o FuzzyBoT fica parado com a luz vermelha acesa, 
depois anda para frente rapidamente com a luz verde acesa e, por fim, reduz a velocidade com a luz amarela acesa.

```blocks
```

## Passo 26
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function sinal_verde () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Green))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Green))
    LEDs.show()
}
function sinal_amarelo () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Yellow))
    LEDs.show()
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function sinal_vermelho () {
    LEDs.setPixelColor(0, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(1, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(2, rgbLed.colors(NeoPixelColors.Red))
    LEDs.setPixelColor(3, rgbLed.colors(NeoPixelColors.Red))
    LEDs.show()
}
let iniciar = 0
let LEDs: rgbLed.Strip = null
let velocidade = 0
LEDs = rgbLed.create(DigitalPin.P15, 4, NeoPixelMode.RGB)
basic.forever(function () {
    if (iniciar == 1) {
        sinal_vermelho()
        basic.pause(3000)
        sinal_verde()
        velocidade = 100
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        basic.pause(1500)
        sinal_amarelo()
        velocidade = 40
        fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        basic.pause(1500)
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
        LEDs.clear()
        LEDs.show()
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```