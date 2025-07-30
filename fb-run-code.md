### @diffs true
# Corra!

## Passo 1
Neste tutorial, vamos compreender o uso do sensor ultrassônico para medições de distâncias com o 
FuzzyBoT. A ideia nesta aplicação é que o FuzzyBoT utilize esse sensor para medir a distância de objetos à sua frente.
Se essa distância for menor que 10cm, então ele deve se movimentar para trás. Ou seja, o FuzzyBoT vai sair 
correndo sempre que um objeto aparecer a menos de 10cm do carrinho.

```template
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Primeiramente, acesse a aba ``||Logic:Lógica||`` e adicione um laço ``||Logic:se então senão||`` dentro do ``||basic:sempre||``.

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
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 4
Volte à aba ``||Logic:Lógica||`` e adicione um bloco comparador ``||Logic:0 = 0||`` para substituir o ``||Logic:verdadeiro||``.
Acesse o menu de ``||variables:Variáveis||`` e selecione o bloco redondo da variável ``||variables:iniciar||`` para 
substituir o primeiro campo do comparador. Em seguida, altere o segundo campo de **0** para **1**.

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
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
    	
    } else {
    	
    }
})
```

## Passo 5
Acesse o menu do ``||fuzzyBot:FuzzyBoT||`` e insira o bloco ``||fuzzyBot:parar motor esquerdo||`` dentro do laço
``||logic:senão||``. Antes de seguir, clique na seta do bloco para alterar de motor ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``.

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
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
    	
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 6
Em seguida, acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**, 
e crie uma variável chamada: ``||variables:distancia||``. 
Em seguida, adicione o bloco ``||variables:definir distancia para 0||``, que
aparecerá ao criá-la, para dentro do ``||Logic:então||`` deste laço.  


```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let distancia = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        distancia = 0
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 7
Retorne ao menu do ``||fuzzyBot:FuzzyBoT||``, selecione o bloco ``||fuzzyBot:sensor ultrassom emissor receptor unidade||`` e posicione-o 
dentro do bloco de definição da variável ``||variables:distancia||``, substituindo o **0**. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let distancia = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        distancia = fuzzyBot.ping(
        DigitalPin.P0,
        DigitalPin.P0,
        PingUnit.MicroSeconds
        )
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 8
Agora, clique nas setas desse bloco para configurar as portas corretas. O pino do ``||fuzzyBot:emissor||`` será **P1**,
enquanto o pino do ``||fuzzyBot:receptor||`` será o **P2**. Altere a unidade de medição de microsegundos para **cm**. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let distancia = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        distancia = fuzzyBot.ping(
        DigitalPin.P1,
        DigitalPin.P2,
        PingUnit.Centimeters
        )
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 9
Feito isso, vamos adicionar um segundo laço ``||Logic:se então senão||``,
dentro do laço ``||Logic:então||`` anterior.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let distancia = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        distancia = fuzzyBot.ping(
        DigitalPin.P1,
        DigitalPin.P2,
        PingUnit.Centimeters
        )
        if (true) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 10
Ele também deve ter um bloco comparador ``||Logic:0 < 0||`` **(menor que)** no lugar do ``||Logic:verdadeiro||``.
Substitua o primeiro campo desse comparador pela variável ``||variables:distancia||`` e modifique o segundo campo
de **0** para **10**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let distancia = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        distancia = fuzzyBot.ping(
        DigitalPin.P1,
        DigitalPin.P2,
        PingUnit.Centimeters
        )
        if (distancia < 10) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 11
Retorne ao menu ``||fuzzyBot:FuzzyBoT||``, selecione o bloco ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||``
e posicione-o dentro do ``||Logic:então||`` deste novo laço.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let distancia = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        distancia = fuzzyBot.ping(
        DigitalPin.P1,
        DigitalPin.P2,
        PingUnit.Centimeters
        )
        if (distancia < 10) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 1)
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 12
Agora, clique nas setas para baixo para alterar os parâmetros desse bloco. Modifique o motor de ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``,
o sentido de ``||fuzzyBot:frente||`` para ``||fuzzyBot:trás||`` e a velocidade para **50**. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let distancia = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        distancia = fuzzyBot.ping(
        DigitalPin.P1,
        DigitalPin.P2,
        PingUnit.Centimeters
        )
        if (distancia < 10) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 13
Por fim, dentro do ``||Logic:senão||`` deste laço, adicione um bloco ``||fuzzyBot:parar motor todos||``,
que pode ser duplicado do ``||Logic:senão||`` de baixo ou encontrado na aba ``||fuzzyBot:FuzzyBoT||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let distancia = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        distancia = fuzzyBot.ping(
        DigitalPin.P1,
        DigitalPin.P2,
        PingUnit.Centimeters
        )
        if (distancia < 10) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
        } else {
        	fuzzyBot.motorStop(fuzzyBot.Motors.All)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 14
Agora seu código está pronto! Baixe-o para o micro:bit e teste-o posicionando um objeto
a menos de 10cm do sensor ultrassônico. Ao fazer isso, o FuzzyBoT deve dar ré, ficando sempre a uma distância igual ou 
menor que 10cm. Se quiser ajustar essa distância, basta trocar o valor do comparador ``||Logic:distancia < 10||``
em seu código. 

```blocks
```

## Passo 15
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let distancia = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        distancia = fuzzyBot.ping(
        DigitalPin.P1,
        DigitalPin.P2,
        PingUnit.Centimeters
        )
        if (distancia < 10) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
        } else {
        	fuzzyBot.motorStop(fuzzyBot.Motors.All)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```
    
```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```