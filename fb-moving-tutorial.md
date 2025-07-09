### @diffs true
# FuzzyBoT em Movimento

## Passo 1
Neste tutorial, vamos iniciar a programação das funções dos movimentos básicos do FuzzyBoT. Em seguida,
vamos entender como combinar esses movimentos para que ele percorra trajetos específicos. Por fim, usaremos os Botões A e B 
do Micro:bit para ligar e desligar o deslocamento do nosso robô. Antes de prosseguir, veja a lista de funções que vamos criar:
1. Avançar;
2. Virar para esquerda;
3. Virar para direita;
4. Virar para esquerda bruscamente;
5. Virar para direita bruscamente;
6. Marcha ré. 
## Passo 2
Para começar, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Vamos iniciar a programação criando duas variáveis: ``||variables:Velocidade||`` e ``||variables:Ligar||``.
Para isso, acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**. Nomeie suas variáveis como 
``||variables:Velocidade||`` e ``||variables:Ligar||``.

```blocks
```

## Passo 4 
Ao fazer isso, blocos de definição dessas variáveis aparecerão no menu ``||variables:Variáveis||``. Adicione dois blocos ``||variables:Definir 'variável' para 0||`` dentro
do laço ``||basic:no iniciar||``. Clique no campo de variáveis dentro desse bloco para selecionar um para ``||variables:Velocidade||`` e outro para ``||variables:Ligar||``.

**Dica:** se o laço ``||basic:no iniciar||`` não estiver presente no seu código automaticamente, você pode encontrá-lo na aba ``||basic:Básico||``.


```blocks
let Velocidade = 0
let Ligar = 0
```

## Passo 5
Modifique o valor de velocidade de **0** para **150**. Esse número determina a velocidade de movimentação do seu FuzzyBoT, pois essa variável será usada nos laços
de cada função criada posteriormente. Ele pode variar de **0** até **1023**. Sugerimos começar com um valor mais baixo, como 150, para entender o comportamento do seu robô.

```blocks
let Velocidade = 150
let Ligar = 0
```

## Passo 6
Agora, acesse a aba ``||input:Entrada||`` e adicione dois laços ``||input:no botão A pressionado||``. Clique em um dos laços para 
modificar o botão de ``||input:Botão A||`` para ``||input:Botão B||``.  

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
let Velocidade = 150
let Ligar = 0
```
## Passo 7
Duplique o bloco ``||variables:Definir Ligar para 0||``, que criamos no laço ``||basic:no iniciar||``, clicando com o botão direito do mouse sobre o bloco. 
Posicione um dentro do laço do ``||input:Botão A||`` e outro no laço do ``||input:Botão B||``. Modifique o valor dessa variável de **0** para **1**
no bloco dentro do ``||input:Botão A||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
let Ligar = 0
let Velocidade = 150
Ligar = 0
```

## Passo 8
Feito isso, presseguimos para a criação das  ``||Functions:Funções||``.
Então, clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada ``||Functions:Avançar||``. Um novo laço referente à função criada é adicionado automaticamente ao código.

```blocks
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
function Avançar () {
	
}
let Ligar = 0
let Velocidade = 150
Ligar = 0
```

## Passo 9
Dentro deste laço, vamos adicionar os comandos para execução do movimento desejado. Nesse caso, acesse a aba
``||fuzzyBot:FuzzyBoT||`` e adicione o bloco ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||`` dentro
do laço da função ``||Functions:Avançar||``.

```blocks
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
}
let Ligar = 0
let Velocidade = 150
Ligar = 0
```

## Passo 10
Clique no bloco para alterar o motor de ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``. Em seguida, 
retorne ao menu ``||variables:Variáveis||`` e arraste o bloco de bordas redondas ``||variables:Velocidade||``
para substituir o valor **0** do bloco do motor. 

```blocks
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
let Ligar = 0
let Velocidade = 0
Velocidade = 150
Ligar = 0
```

## Passo 11
Agora, vamos repetir o processo de criação de  ``||Functions:Funções||`` para criar a função ``||Functions:Virar_esquerda||``.
Você também pode duplicar o laço da função ``||Functions:Avançar||`` com o botão direito do mouse e alterar o seu nome.

```blocks
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
function Virar_esquerda () {
	
}
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
let Ligar = 0
let Velocidade = 0
Velocidade = 150
Ligar = 0
```

## Passo 12
Dentro dessa função, precisaremos de dois blocos de controle dos motores do FuzzyBoT: ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||``. 
Edite um dos blocos para que um deles controle o motor ``||fuzzyBot:esquerdo||`` e outro o ``||fuzzyBot:direito||``.

```blocks
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
let Ligar = 0
let Velocidade = 0
Velocidade = 150
Ligar = 0
```

## Passo 13
Para realizar esse movimento para esquerda, vamos manter o motor ``||fuzzyBot:esquerdo||`` parado e o ``||fuzzyBot:direito||`` movimentando
com o valor da variável ``||variables:Velocidade||``.

```blocks
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
let Ligar = 0
let Velocidade = 0
Velocidade = 150
Ligar = 0
```

## Passo 14
Agora, vamos replicar o processo para a função de ``||Functions:Virar_direita||``. O modo mais prático é
simplesmente duplicar o laço da função ``||Functions:Virar_esquerda||`` e renomeá-lo. Feito isso, inverta os 
motores ``||fuzzyBot:esquerdo||`` e ``||fuzzyBot:direito||`` para que o direito fique parado enquanto o esquerdo gira
com o valor da variável ``||variables:Velocidade||``.

```blocks
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 15
Para as funções das curvas bruscas, vamos fazer com que o motor que ficava parado em cada caso, gire para o sentido inverso do outro.
Assim, o raio da curva diminuirá. Vamos começar pela função ``||Functions:Virar_esquerda_brusca||``. Duplique todo o laço 
``||Functions:Virar_esquerda||`` e altere seu nome.

```blocks
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 16
Em seguida, edite o bloco do motor ``||fuzzyBot:esquerdo||`` para que ele se movimente para ``||fuzzyBot:trás||`` e também
com o valor da variável ``||variables:Velocidade||``.

```blocks
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, Velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 17
Agora, vamos duplicar o laço ``||Functions:Virar_direita||``, renomeá-lo para ``||Functions:Virar_direita_brusca||`` e alterar o bloco do motor 
``||fuzzyBot:direito||`` para que ele se movimente para ``||fuzzyBot:trás||`` e também
com o valor da variável ``||variables:Velocidade||``.

```blocks
function Virar_direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, Velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 18
Por fim, vamos criar a última função: ``||Functions:Marcha ré||``. O método mais rápido é simplesmente
duplicar a função ``||Functions:Avançar||``, renomeá-la e alterar o sentido do motor para ``||fuzzyBot:trás||``.

```blocks
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function Marcha_ré () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, Velocidade)
}
```

## Passo 19
Com todas as funções de movimento prontas, podemos prosseguir para combiná-las dentro de um laço ``||basic:sempre||``, localizado
na aba ``||basic:Básico||``.

```blocks
basic.forever(function () {
    
})
```



## Passo 20
Acesse o menu ``||logic:Lógica||`` e insira o laço condicional ``||logic:se-então-senão||`` dentro do ``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 21
Retorne à aba ``||logic:Lógica||`` e adicione o bloco comparador ``||logic:0 = 0||`` dentro do campo **verdadeiro** do ``||logic:se-então-senão||``.
Altere o primeiro valor da comparação de **0** para a variável ``||variables:Ligar||``, e o segundo valor de **0** para **1**.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
    	
    } else {
    	
    }
})
```

## Passo 22
Agora, dentro do ``||logic:então||``, podemos combinar os movimentos desejados. Para isso, comece acessando 
``||Advanced:Avançado||``, clique em ``||Functions:Funções||`` e selecione o comando ``||Functions:ligar Avançar||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Avançar()
    } else {
    	
    }
})
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 23
Em seguida, acesse a aba ``||basic:Básico||`` e adicione um bloco ``||basic:pausa (ms) 100||`` após a chamada da função para 
determinar por quanto tempo ela será executada antes do próximo movimento. Altere seu valor de **100 ms** para **1000 ms** (1 segundo).
```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Avançar()
        basic.pause(1000)
    } else {
    	
    }
})
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 24
Vamos replicar essa lógica para chamar a função ``||Functions:Virar_esquerda||`` por ``||basic: 600 (ms)||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Avançar()
        basic.pause(1000)
        Virar_esquerda()
        basic.pause(600)
    } else {
    	
    }
})
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 25
Agora, adicione outro movimento de ``||Functions:Avançar||`` por ``||basic: 1000 (ms)||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Avançar()
        basic.pause(1000)
        Virar_esquerda()
        basic.pause(600)
        Avançar()
        basic.pause(1000)
    } else {
    	
    }
})
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 26
Vamos aproveitar para incluir um movimento de curva brusca, como o ``||Functions:Virar_direita_brusca||`` por ``||basic: 200 (ms)||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Avançar()
        basic.pause(1000)
        Virar_esquerda()
        basic.pause(600)
        Avançar()
        basic.pause(1000)
        Virar_direita_brusca()
        basic.pause(200)
    } else {
    	
    }
})
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, Velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 27
Adicione mais um movimento de ``||Functions:Avançar||`` por ``||basic: 1000 (ms)||`` após a curva brusca.
Feito isso, acrescente um bloco ``||variables:Definir Ligar para 0||``, disponível no menu ``||Functions:Variáveis||``.  

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Avançar()
        basic.pause(1000)
        Virar_esquerda()
        basic.pause(600)
        Avançar()
        basic.pause(1000)
        Virar_direita_brusca()
        basic.pause(200)
        Avançar()
        basic.pause(1000)
        Ligar = 0
    } else {
    	
    }
})
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, Velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 28
Para finalizar, acesse a aba ``||fuzzyBot:FuzzyBoT||`` e insira o comando ``||fuzzyBot:parar motor esquerdo||`` dentro do ``||logic:senão||`` do laço ``||logic:se-então-senão||``.
Modifique o controle de motor ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Avançar()
        basic.pause(1000)
        Virar_esquerda()
        basic.pause(600)
        Avançar()
        basic.pause(1000)
        Virar_direita_brusca()
        basic.pause(200)
        Avançar()
        basic.pause(1000)
        Ligar = 0
    } else {
    	fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, Velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 29
Agora seu código está pronto! Baixe-o para o micro:bit, e teste a movimentação pressionando o botão A para inciar o trajeto.
Fique à vontade para testar outras combinações de movimentos ou ajustar as temporizações de cada um deles.
Pense nas funções de movimento como ingredientes que podem ser combinados de infinitas formas para percorrer seus trajetos.

```blocks
```

## Passo 28
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
function Virar_esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, Velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
function Virar_direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, Velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, Velocidade)
}
function Virar_esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, Velocidade)
}
function Marcha_ré () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, Velocidade)
}
function Avançar () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
let Ligar = 0
let Velocidade = 0
Velocidade = 150
Ligar = 0
basic.forever(function () {
    if (Ligar == 1) {
        Avançar()
        basic.pause(1000)
        Virar_esquerda()
        basic.pause(600)
        Avançar()
        basic.pause(1000)
        Virar_direita_brusca()
        basic.pause(200)
        Avançar()
        basic.pause(1000)
        Ligar = 0
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```