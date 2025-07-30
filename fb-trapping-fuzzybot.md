### @diffs true
# Prendendo o FuzzyBoT

## Passo 1 - teste
Neste tutorial, vamos aprender como utilizar os três sensores infravermelhos na parte inferior do chassi do FuzzyBoT.
Eles são especialmente úteis para identificar linhas pretas no chão, permitindo a construção de seguidores de linha.
Nessa atividade, vamos criar uma função para interpretar o que os sensores estão identificado e manter o FuzzyBoT preso de 
uma área fechada por linhas pretas.

## Passo 2
Se os sensores não estiverem identificando uma linha preta, o FuzzyBoT está livre para andar para frente. Entretanto,
se ele identificar alguma linha, o FuzzyBoT deve andar para trás e virar para alguma direção aleatória antes de seguir novamente.

## Passo 3
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 4
Primeiramente, vamos configurar o micro:bit para nos indicar que ele foi ligado corretamente. Para isso, acesse a aba ``||Basic:Básico||`` e 
adicione os comandos ``||Basic:mostrar ícone||`` e ``||Basic:pausa (ms)||`` dentro do laço ``||Basic:no iniciar||``.
Em seguida, altere o valor de ``||Basic:pausa||`` de **100ms** para **1000ms** (1 segundo).

 **Obs.:** Se o laço ``||basic:no iniciar||`` não estiver em seu código automaticamente, você pode encontrá-lo na aba ``||Basic:Básico||``.

```blocks
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 5
Acesse o menu ``||Input:Input||`` e adicione dois laços ``||Input:no botão A pressionado||`` à sua área de programação.
Altere um dos laços de ``||Input:botão A||`` para ``||Input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 6
Em seguida, acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Vamos criar três variáveis chamadas: ``||variables:direcao||``, ``||variables:status_SL||`` e ``||variables:iniciar||``. 
Por fim, adicione o bloco ``||variables:definir iniciar para 0||`` que
aparecerá ao criá-la para dentro dos laços ``||Input:no botão A pressionado||`` e ``||Input:no botão B pressionado||``.  

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 0
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
})
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 7
Agora, altere de **0** para **1** o valor da variável ``||variables:iniciar||`` dentro do primeiro laço: ``||Input:no botão A pressionado||``.
Vamos aproveitar para adicionar um feedback ao usuário quando esses botões forem pressionados. Para isso,
acesse o menu ``||Basic:Básico||`` e adicione um comando ``||Basic:mostrar ícone||`` para cada laço. Altere o ícone 
do laço do ``||Input:botão A||`` para um **check** e do ``||Input:botão B||`` para um **X**.

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
	
})
```

## Passo 8
Feito isso, vamos criar uma ``||Functions:Função||`` para ler os três sensores infravermelhos.
Para isso, clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada ``||Functions:seguidor_linha||``. 
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
function seguidor_linha () {
	
}
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 9
Acesse o menu ``||Logic:Lógica||`` e adicione um laço ``||Logic:Se verdadeiro então||`` dentro do laço da ``||Functions:Função||``.
Retorne à aba ``||Logic:Lógica||`` e adicione dois operadores Booleandos ``||Logic:E||`` dentro do campo **verdadeiro** do laço ``||Logic:Se então||``.
Um operador deve ser inserido dentro do outro, resultando em três campos de bordas triangulares. *(um campo para cada sensor)*

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (false && (false && false)) {
    	
    }
}
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 10
Agora, dentro de **cada** campo triangular, vamos adicionar um bloco comparador ``||Logic:0 = 0||``, também localizado na aba ``||Logic:Lógica||``.
Tenha cuidado ao inseri-los para não substituir um dos blocos ``||Logic:E||``. No total, deveremos ter **seis** campos redondos com o valor **0** por enquanto.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (0 == 0 && (0 == 0 && 0 == 0)) {
    	
    }
}
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 11
Feito isso, vamos substituir o primeiro campo de cada comparador pelo bloco ``||fuzzyBot:ler sensor de linha esquerdo||``.
Depois de adicioná-los em cada comparador, clique na seta do segundo e do terceiro bloco para alterar de ``||fuzzyBot:sensor esquerdo||`` 
para ``||fuzzyBot:sensor meio||`` e ``||fuzzyBot:sensor direito||`` respectivamente.

 **Dica:** Clique no ícone da lâmpada para verificar seu código. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
    	
    }
}
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 12
Com as condições determinadas, acesse a aba ``||variables:Variáveis||`` e inclua o bloco ``||variables:definir status_SL para 0||`` dentro do ``||Logic:então||``.
Se esse bloco não estiver aparecendo, basta incluir o bloco de definição de variável que aparecer em seu menu, clicar na seta para baixo e escolher qual variável você deseja,
neste caso, a variável ``||variables:status_SL||``. Ela vai nos indicar como está a identificação dos sensores seguidores de linha.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 13
Agora vamos programar uma segunda possibilidade de identificação dos sensores. Para isso, clique **duas vezes** no sinal de **+** do laço ``||Logic:se verdadeiro então||``
para criar um segundo campo de bordas triangulares, formando ``||Logic:senão se falso então||``.

 **Dica:** Clique no ícone da lâmpada para verificar seu código. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (false) {
    	
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 14
Clique com o botão direito do mouse próximo do ``||Logic:E||`` para selecionar e duplicar o maior bloco de bordas triangulares,
que inclui todos os sensores nos três comparadores. Insira o novo bloco dentro do campo triangular do ``||Logic:senão se falso então||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
    	
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 15
Agora, altere apenas o último campo redondo, do ``||fuzzyBot:sensor direito||`` de **0** para **1**.
Em seguida, duplique o bloco ``||variables:definir status_SL para 0||``, coloque-o dentro do novo ``||Logic:então||`` 
e altere seu valor de **0** para **1**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 16
Clique mais uma vez no sinal de **+** abaixo do ``||Logic:senão||`` para adicionar outro caso. Como fizemos no passo anterior,
duplique o grande bloco de bordas triangulares com todos os comparadores e insira dentro desse novo laço. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
    	
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 17
Feito isso, altere o valor do ``||fuzzyBot:sensor meio||`` de **0** para **1** e o do ``||fuzzyBot:sensor direito||`` de **1** para **0**.
Assim, teremos os sensores com os valores: **0   1   0**.

 Em seguida, duplique o bloco ``||variables:definir status_SL para 0||``, coloque-o dentro do novo ``||Logic:então||`` 
e altere seu valor para **2**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 18
Seguiremos com essa lógica para contemplar todos os casos possíveis de detecção dos sensores!
Clique mais uma vez no sinal de **+** abaixo do ``||Logic:senão||`` para adicionar outro caso. Como fizemos no passo anterior,
duplique o grande bloco de bordas triangulares com todos os comparadores e insira dentro desse novo laço. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
    	
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 19
Feito isso, altere o valor do ``||fuzzyBot:sensor direito||`` de **0** para **1**.
Assim, teremos os sensores com os valores: **0   1   1**.

 Em seguida, duplique o bloco ``||variables:definir status_SL para 0||``, coloque-o dentro do novo ``||Logic:então||`` 
e altere seu valor para **3**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 20
Clique mais uma vez no sinal de **+** abaixo do ``||Logic:senão||`` para adicionar outro caso. Duplique o grande bloco de bordas triangulares com todos os comparadores e insira dentro desse novo laço. 


```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
    	
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 21
Feito isso, altere o valor do ``||fuzzyBot:sensor esquerdo||`` de **0** para **1**, e do ``||fuzzyBot:sensor meio||`` e  ``||fuzzyBot:sensor direito||``
de **1** para **0**.
Assim, teremos os sensores com os valores: **1   0   0**.

 Em seguida, duplique o bloco ``||variables:definir status_SL para 0||``, coloque-o dentro do novo ``||Logic:então||`` 
e altere seu valor para **4**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 22
Clique mais uma vez no sinal de **+** abaixo do ``||Logic:senão||`` para adicionar outro caso. Duplique o grande bloco de bordas triangulares com todos os comparadores e insira dentro desse novo laço. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
    	
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 23
Feito isso, altere o valor do ``||fuzzyBot:sensor direito||`` de **0** para **1**.
Assim, teremos os sensores com os valores: **1   0   1**.

 Em seguida, duplique o bloco ``||variables:definir status_SL para 0||``, coloque-o dentro do novo ``||Logic:então||`` 
e altere seu valor para **5**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 24
Calma! Estamos quase lá! Clique mais uma vez no sinal de **+** abaixo do ``||Logic:senão||`` para adicionar outro caso. Duplique o grande bloco de bordas triangulares com todos os comparadores e insira dentro desse novo laço. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
    	
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 25
Feito isso, altere o valor do ``||fuzzyBot:sensor meio||`` de **0** para **1** e do ``||fuzzyBot:sensor direito||`` de **1** para **0**.
Assim, teremos os sensores com os valores: **1   1   0**.

 Em seguida, duplique o bloco ``||variables:definir status_SL para 0||``, coloque-o dentro do novo ``||Logic:então||`` 
e altere seu valor para **6**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 26
Finalmente, chegamos ao último caso, mas esse é um pouco diferente!
Clique mais uma vez no sinal de **+** abaixo do ``||Logic:senão||`` para adicionar outro caso. Antes de prosseguir, clique no último sinal de **-** para 
apagar o laço ``||Logic:senão||``. Depois disso, duplique o grande bloco de bordas triangulares com todos os comparadores e insira dentro desse novo laço. 

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
    	
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 27
Feito isso, altere o valor do ``||fuzzyBot:sensor direito||`` de **0** para **1**.
Assim, teremos os sensores com os valores: **1   1   1**.

 Em seguida, duplique o bloco ``||variables:definir status_SL para 0||``, coloque-o dentro do novo ``||Logic:então||`` 
e altere seu valor para **7**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
	
})
```

## Passo 28
Agora, vamos criar os comandos de movimentação do FuzzyBoT a partir do que foi identificado pelos sensores.
A partir de agora, trabalharemos dentro do laço ``||basic:sempre||``, que pode ser encontrado dentro do menu ``||basic:Básico||``.
Comece adicionando um laço ``||Logic:se então senão||`` dentro do ``||basic:sempre||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 29
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
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
    	
    } else {
    	
    }
})
```

## Passo 30
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
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let status_SL = 0
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

## Passo 31
Agora, vamos programar o que ficará dentro do ``||logic:então||``. Primeiramente, acesse o menu 
de ``||Functions:Funções||``, dentro de ``||Advanced:Avançado||`` e adicione o comando ``||Functions:ligar seguidor_linha||``
dentro do ``||logic:então||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 32
Feito isso, vamos adicionar um segundo laço ``||Logic:se então senão||`` abaixo desse bloco ``||Functions:ligar seguidor_linha||``,
ainda dentro do laço ``||Logic:então||`` anterior.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (true) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 33
Ele também deve ter um bloco comparador ``||Logic:0 = 0||`` no lugar do ``||Logic:verdadeiro||``.
Substitua o primeiro campo desse comparador pela variável ``||variables:status_SL||`` e o segundo campo
de **0** por **7**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 34
Dentro do ``||Logic:então||`` desse laço, inclua o comando ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||``, localizado na 
aba ``||fuzzyBot:FuzzyBoT||``. Clique na seta para alterar o motor de ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``.
Em seguida, modifique o valor de velocidade de **0** para **50**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 35
Agora, acesse a aba ``||variables:Variáveis||``, selecione o bloco ``||variables:definir direcao para 0||`` e o insira dentro do laço
``||logic:senão||`` abaixo do bloco que posicionamos no passo anterior. Se a variável do seu bloco de definição estiver diferente, clique na seta
para baixo e escolha a variável ``||variables:direcao||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 36
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
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let direcao = 0
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
            direcao = randint(0, 1)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 37
Em seguida, duplique o bloco ``||fuzzyBot:Motor todos mover para frente com a velocidade 50||`` e cole o novo abaixo
do bloco de definição da variável. Clique na seta do meio do bloco para alterar o sentido de rotação de ``||fuzzyBot:frente||`` para ``||fuzzyBot:trás||``.
Acesse a aba ``||Basic:Básico||`` e adicione um bloco de ``||Basic:pausa (ms)||`` após o controle de motores.
Modifique a duração da pausa de **100ms** para **500ms**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let direcao = 0
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
            direcao = randint(0, 1)
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
            basic.pause(500)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 38
Ainda dentro desse ``||Logic:senão||``, abaixo da ``||Basic:pausa||``, acrescente outro laço ``||Logic:se então senão||``.
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
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let direcao = 0
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
            direcao = randint(0, 1)
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
            basic.pause(500)
            if (true) {
            	
            } else {
            	
            }
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 39
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
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let direcao = 0
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
            direcao = randint(0, 1)
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
            basic.pause(500)
            if (direcao == 0) {
            	
            } else {
            	
            }
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 40
Dentro do ``||Logic:então||`` deste laço, duplique o bloco ``||fuzzyBot:Motor todos mover para trás com a velocidade 50||`` e altere
o motor de ``||fuzzyBot:todos||`` para ``||fuzzyBot:direito||``. Em seguida, acesse o menu ``||fuzzyBot:FuzzyBoT||`` e adicione o comando 
``||fuzzyBot:parar motor esquerdo||`` abaixo desse bloco. Por fim, adicione uma ``||basic:pausa||`` com a duração de **300ms**.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let direcao = 0
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
            direcao = randint(0, 1)
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
            basic.pause(500)
            if (direcao == 0) {
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorStop(fuzzyBot.Motors.M1)
                basic.pause(300)
            } else {
            	
            }
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 41
Prosseguindo para o ``||Logic:senão||`` deste laço, duplique todos os três laços do ``||Logic:então||`` anterior e cole-os no ``||Logic:senão||``.
Entretanto, inverta os motores controlados: no primeiro bloco altere de ``||fuzzyBot:motor direito||`` para ``||fuzzyBot:motor esquerdo||`` e no segundo 
bloco, ``||fuzzyBot:pare motor direito||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let direcao = 0
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
            direcao = randint(0, 1)
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
            basic.pause(500)
            if (direcao == 0) {
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorStop(fuzzyBot.Motors.M1)
                basic.pause(300)
            } else {
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorStop(fuzzyBot.Motors.M2)
                basic.pause(300)
            }
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 42
Agora seu código está pronto! Baixe-o para o micro:bit e posicione o FuzzyBoT dentro de uma área
delimitada por fitas pretas no chão, como fita isolante. Verifique se ele ficará preso dentro das linhas.

```blocks
```

## Passo 43
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
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0)) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1)) {
        status_SL = 7
    }
}
let direcao = 0
let status_SL = 0
let iniciar = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
            direcao = randint(0, 1)
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
            basic.pause(500)
            if (direcao == 0) {
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorStop(fuzzyBot.Motors.M1)
                basic.pause(300)
            } else {
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorStop(fuzzyBot.Motors.M2)
                basic.pause(300)
            }
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```