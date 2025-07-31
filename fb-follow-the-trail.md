### @diffs true
# Siga a Trilha

## Passo 1
Neste tutorial, vamos combinar a identificação dos sensores seguidores de linha com as funções de movimento do primeiro
projeto que fizemos com o FuzzyBoT. Para facilitar, já mantivemos as funções de leitura dos sensores e de movimentação prontas,
visto que já aprendemos como criá-las em atividades anteriores. Nosso foco será no desenvolvimento da lógica dentro do laço
``||basic:sempre||``.

```template
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Primeiramente, acesse o menu ``||Functions:Funções||``, dentro de ``||Advanced:Avançado||`` e adicione o comando ``||Functions:ligar seguidor_linha||``
dentro do ``||basic:sempre||``.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
})
```

## Passo 4
Feito isso, adicione um laço ``||Logic:se então senão||`` dentro do ``||basic:sempre||``.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 5
Volte à aba ``||Logic:Lógica||`` e adicione um bloco comparador ``||Logic:0 = 0||`` para substituir o ``||Logic:verdadeiro||``.
Acesse o menu de ``||variables:Variáveis||`` e selecione o bloco redondo da variável ``||variables:iniciar||`` para 
substituir o primeiro campo do comparador. Em seguida, altere o segundo campo de **0** para **1**.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
    	
    } else {
    	
    }
})
```

## Passo 6
Acesse o menu do ``||fuzzyBot:FuzzyBoT||`` e insira o bloco ``||fuzzyBot:parar motor esquerdo||`` dentro do laço
``||logic:senão||``. Antes de seguir, clique na seta do bloco para alterar de motor ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
    	
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 7
Feito isso, vamos adicionar um segundo laço ``||Logic:se então senão||``,
dentro do laço ``||Logic:então||`` anterior.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
    	
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 8
Ele também deve ter um bloco comparador ``||Logic:0 = 0||`` no lugar do ``||Logic:verdadeiro||``.
Substitua o primeiro campo desse comparador pela variável ``||variables:status_SL||``.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 9
Dentro do ``||Logic:então||`` desse laço, adicione o comando ``||Functions:Ligar frente||``, localizado no menu de
``||Functions:Funções||``, dentro de ``||Advanced:Avançado||``. 

 **Obs.:** Neste caso, estamos programando a situação em que nenhum sensor está recebendo reflexos dos raios infravermelhos que emitem.
 Isso significa que todos os três estão sobre a fita preta, que absorve esses raios, impossibilitando a reflexão. Portanto, o FuzzyBoT deve seguir
 em frente sobre essa linha.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 10
Clique no sinal de **+** abaixo do ``||Logic:senão||`` deste laço para adicionar um segundo teste condicional.
Neste novo teste, duplique o comparador anterior,  ``||Logic:status_SL = 0||``, e cole-o no novo campo de bordas triangulares. 
Altere o segundo valor do comparador de **0** para **1**.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 11
Quando a variável ``||variables:status_SL||`` é igual a **1** significa que o ``||fuzzyBot:sensor de linha direito||`` começou a 
receber sinais de reflexão dos raios infravermelhos. Ou seja, ele saiu de cima da linha preta. Portanto, precisamos
programar o FuzzyBoT para ir para a esquerda utilizando o comando ``||Functions:Ligar esquerda||``, localizado no menu de
``||Functions:Funções||``, dentro de ``||Advanced:Avançado||``. 

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 12
Vamos clicar novamente no sinal de **+** para adicionar o caso em que ``||Logic:status_SL = 3||``.
Logo, depois de duplicar o comparador, lembre-se de alterar o segundo valor para **3**.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 13
Nessa situação, o ``||fuzzyBot:sensor meio||`` e ``||fuzzyBot:sensor direito||`` saíram de cima da fita preta.
Portanto, devemos direcionar o FuzzyBoT bruscamente para a esquerda utilizando o comando ``||Functions:Ligar esquerda_brusca||``, localizado no menu de
``||Functions:Funções||``, dentro de ``||Advanced:Avançado||``. 

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 14
Clique novamente no sinal de **+** para criar a condição em que ``||Logic:status_SL = 4||``.
Ao duplicar, lembre-se de alterar o segundo valor do comparador para **4**.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 15
Neste caso, o ``||fuzzyBot:sensor esquerdo||`` saiu de cima da fita preta.
Portanto, devemos direcionar o FuzzyBoT para a direita utilizando o comando ``||Functions:Ligar direita||``, localizado no menu de
``||Functions:Funções||``, dentro de ``||Advanced:Avançado||``.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 16
Por fim, clique novamente no sinal de **+** para adicionar o caso em que ``||Logic:status_SL = 6||``.
Ao duplicar, lembre-se de alterar o segundo valor do comparador para **6**. Antes de prosseguir,
clique no sinal de **-** à frente do ``||Logic:senão||`` para apagar esse laço vazio.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 17
Nessa última possibilidade, o ``||fuzzyBot:sensor meio||`` e ``||fuzzyBot:sensor esquerdo||`` saíram de cima da fita preta.
Portanto, devemos direcionar o FuzzyBoT bruscamente para a direita utilizando o comando ``||Functions:Ligar direita_brusca||``, localizado no menu de
``||Functions:Funções||``, dentro de ``||Advanced:Avançado||``. 

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 18
Agora seu código está pronto! Baixe-o para o micro:bit e posicione o FuzzyBoT sobre uma linha
na cor preta para que ele siga essa trilha. Pressione o botão A para ele iniciar o movimento.
É importante que essa fita tenha uma largura suficiente para, pelo menos, abranger os três sensores
embaixo do chassi.

```blocks
```

## Passo 19
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    iniciar = 0
    basic.showIcon(IconNames.No)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
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
    seguidor_linha()
    if (iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```