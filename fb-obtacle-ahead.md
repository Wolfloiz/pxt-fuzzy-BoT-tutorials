### @diffs true
# Obstáculo à Frente

## Passo 1
Neste tutorial, vamos nos aprofundar no uso do sensor ultrassônico e, ao invés de apenas se afastar para longe do obstáculo,
o FuzzyBoT deverá virar para alguma direção aleatória e reiniciar o movimento para frente nessa nova trajetória.
Para facilitar, vamos partir do código que já construímos no projeto "Corra!". 

```template
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

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Vamos iniciar as alterações dentro do laço ``||Logic:se então||``, onde testamos se ``||variables:distancia||`` é **< 10**.
Delete os blocos ``||fuzzyBot:Motor todos mover para trás com a velocidade 50||`` dentro do ``||Logic:então||`` e 
o bloco ``||fuzzyBot:parar motor todos||`` dentro do ``||Logic:senão||``.

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

## Passo 4
Dentro do ``||Logic:senão||`` deste laço, adicione o bloco ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||``.
Clique na seta para baixo para alterar de ``||fuzzyBot:motor esquerdo||`` para ``||fuzzyBot:todos||`` e 
modifique a velocidade de **0** para **50**.

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
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```


## Passo 5
Em seguida, acesse o menu ``||variables:Variáveis||``, clique em **"Fazer uma variável..."**, 
e crie uma variável chamada: ``||variables:direcao||``. 
Em seguida, adicione o bloco ``||variables:definir direcao para 0||``, que
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
let direcao = 0
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
            direcao = 0
        } else {
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 6
O valor da variável ``||variables:direcao||`` deve ser escolhido aleatoriamente entre 0 e 1. Para implementar isso,
acesse o menu ``||math:Matemática||`` e insira o bloco ``||math:escolher aleatório 0 até 10||`` dentro do bloco de definição da variável, 
substituindo o **0**. Altere o segundo valor desse bloco de **10** para **1**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let direcao = 0
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
            direcao = randint(0, 1)
        } else {
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 7
Feito isso, acesse menu do ``||fuzzyBot:FuzzyBoT||`` e adicione o comando ``||fuzzyBot:parar motor esquerdo||`` abaixo do bloco de
definição da variável ``||variables:direcao||``, ainda dentro do ``||Logic:então||``. Clique na seta para baixo para alterar de 
``||fuzzyBot:motor esquerdo||`` para ``||fuzzyBot:todos||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let direcao = 0
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
            direcao = randint(0, 1)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 8
Acrescente uma ``||basic:pausa (ms) 100||``, encontrada na aba ``||basic:Básico||``, abaixo do comando de parar os motores.
Altere a duração da ``||basic:pausa||`` de **100ms** para **700ms**. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let direcao = 0
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
            direcao = randint(0, 1)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            basic.pause(700)
        } else {
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 9
Ainda dentro desse ``||Logic:então||``, abaixo da ``||Basic:pausa||``, acrescente outro laço ``||Logic:se então senão||``.
Preste muita atenção no local desse laço, garantindo que ele esteja dentro do ``||Logic:senão||``. Se necessário, clique na
lâmpada de dica para verificar seu código.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let direcao = 0
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
            direcao = randint(0, 1)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            basic.pause(700)
            if (true) {
            	
            } else {
            	
            }
        } else {
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 10
Adicione um bloco comparador ``||Logic:0 = 0||`` para substituir o verdadeiro desse laço.
No primeiro campo desse comparador, insira o bloco da variável  ``||variables:direcao||``. O segundo
campo pode ser mantido como zero.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let direcao = 0
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
            direcao = randint(0, 1)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            basic.pause(700)
            if (direcao == 0) {
            	
            } else {
            	
            }
        } else {
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 11
Dentro do ``||Logic:então||`` deste laço, adicione o bloco ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||`` e altere
o motor de ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:direito||``, o sentido de rotação de ``||fuzzyBot:frente||`` para ``||fuzzyBot:trás||`` e
a velocidade de **0** para **50**. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let direcao = 0
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
            direcao = randint(0, 1)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            basic.pause(700)
            if (direcao == 0) {
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
            } else {
            	
            }
        } else {
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 12
Em seguida, acesse o menu ``||fuzzyBot:FuzzyBoT||`` e adicione o comando 
``||fuzzyBot:parar motor esquerdo||`` abaixo desse bloco. Por fim, adicione uma ``||basic:pausa||`` com a duração de **700ms**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let direcao = 0
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
            direcao = randint(0, 1)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            basic.pause(700)
            if (direcao == 0) {
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorStop(fuzzyBot.Motors.M1)
                basic.pause(700)
            } else {
            	
            }
        } else {
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 13
Prosseguindo para o ``||Logic:senão||`` deste laço, duplique todos os três laços do ``||Logic:então||`` anterior e cole-os no ``||Logic:senão||``.
Entretanto, inverta os motores controlados: no primeiro bloco altere de ``||fuzzyBot:motor direito||`` para ``||fuzzyBot:motor esquerdo||`` e no segundo 
bloco, ``||fuzzyBot:pare motor direito||``, garantindo que o movimento será o inverso do anterior.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
let direcao = 0
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
            direcao = randint(0, 1)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            basic.pause(700)
            if (direcao == 0) {
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorStop(fuzzyBot.Motors.M1)
                basic.pause(700)
            } else {
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorStop(fuzzyBot.Motors.M2)
                basic.pause(700)
            }
        } else {
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 14
Agora seu código está pronto! Baixe-o para o micro:bit e teste a capacidade do 
FuzzyBoT evitar obstáculos. Ao encontrar um obstáculo a menos de 10cm, ele deve parar,
girar para uma direção aleatória e seguir em linha reta até encontrar outros obstáculos.

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
let direcao = 0
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
            direcao = randint(0, 1)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            basic.pause(700)
            if (direcao == 0) {
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorStop(fuzzyBot.Motors.M1)
                basic.pause(700)
            } else {
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorStop(fuzzyBot.Motors.M2)
                basic.pause(700)
            }
        } else {
        	fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
