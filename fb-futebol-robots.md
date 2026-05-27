### @diffs true
# Contando Voltas

## Passo 1
Neste tutorial, vamos acrescentar ao seguidor de linha duas funções para
tornar o Robô mais robusto. O projeto consiste em manter o robô percorrendo um caminho quadrado,
contando quantas voltas ele completa no período. Teremos descontinuidades 
da linha durante o caminho, uma dificuldade a mais em relação aos projetos anteriores.
Começamos o código a partir do projeto do seguidor de linha.

```template
let Iniciar = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3

Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:encontra_linha||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.
Essa função será chamada antes do robô começar a percorrer o percurso com o objetivo de eliminar o ruído
que pode atrapalhar o sensor no início das leituras, ela garante que  o robô comece
o movimento após encontrar a linha.

```blocks
let Iniciar = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
	
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 4
Acesse a aba ``||loops:Loops||`` e adicione um bloco ``||loops:enquanto executar||`` na função ``||functions:encontra_linha||``.


```blocks
let Iniciar = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (false) {
    	
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 5
Acesse a aba ``||logic:Lógica||`` e selecione o comparador
``||logic:0<0||``. Posicione o bloco no lugar da condição ``||logic:falso||`` 
```blocks
let Iniciar = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (0 < 0) {
    	
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 6
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:contador||``.
Atualize o primeiro valor do comparador com a variável e o segundo valor com **50**.

```blocks
let Iniciar = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    let contador = 0
    while (contador < 50) {
    	
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 7
Adicione o bloco ``||FuzzyBoT:Motor esquerdo mover para frente com a velocidade 0||``
diretamente da aba ``||Fuzzybot:Fuzzybot||``. 
Modifique o valor da velocidade para **50**.

```blocks
let Iniciar = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    let contador = 0
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 8
Duplique o bloco adicionado do passo anterior e coloque a cópia logo embaixo do mesmo.
Altere o motor para **direito** e o sentido para **trás**, criando o bloco
``||FuzzyBoT:Motor direito mover para trás com velocidade 50||``.

```blocks
let Iniciar = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    let contador = 0
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 9
Em seguida, arraste um bloco ``||variables:alterar contador por 1||`` 
para baixo do acionamento dos motores. 


```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 10
Vá ao menu ``||basic:Básico||``, e adicione um bloco ``||basic:pausa (ms) 100||``
após o incremento da variável. Mude o tempo da pausa para **50**.
```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 11
Acesse o menu de ``||Functions:Funções||``, dentro de ``||Advanced:Avançado||``
e adicione o comando ``||Functions:ligar seguidor_linha||``
depois da pausa.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 12
Na aba ``||logic:Lógica||``, clique na condicional ``||logic:se então||`` e
arraste para depois da chamada da função.


```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (true) {
        	
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 13
Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 = 0||``
e substitua a condição **verdadeiro** da condicional.
Atualize os campos do comparador. Vá até a aba ``||variables:Variáveis||``,
clique no bloco ``||variables:status_SL||`` e troque o primeiro **0** do comparador. 


```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
        	
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 14
Acesse a categoria ``||variables:Variáveis||``, pegue o bloco
 ``||variables:definir contador para 0||``
e insira-a dentro da condicional criada nos passos anteriores. 
Altere a definição para o valor **50**, assim garantimos que a linha preta foi encontrada e
saímos do laço.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 15

Volte à seção ``||logic:Lógica||`` para pegar outra condicional ``||logic:se então||``,
adicione-a abaixo da condicional anterior.


```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (true) {
        	
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 16

Ainda no menu ``||logic:Lógica||`` , pegue o bloco booleano ``||logic:" " e " "||`` e substitua a condição **verdadeiro**.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (false && false) {
        	
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 17
Preencha os espaços vazios do booleano com dois blocos condicionais ``||logic: 0 = 0||``.


```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (0 == 0 && 0 == 0) {
        	
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
Vamos atualizar os campos dos comparadores. Acesse a aba ``||variables:Variáveis||``,
pegue a variável ``||variables:status_SL||`` e substitua o primeiro campo do primeiro comparador.
Modifique o segundo campo do comparador para **7**.

Acesse outra vez a aba ``||variables:Variáveis||``,
pegue a variável ``||variables:contador||`` e substitua o primeiro campo do segundo comparador.
Modifique o segundo campo do comparador para **50**.


```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
        	
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
## Passo 19
Dentro do último ``||logic:se então||`` coloque um bloco ``||FuzzyBoT:parar motor todos||``.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
## Passo 20
Adicione a partir do menu ``||loops:Loops||`` um bloco ``||loops:enquanto executar||``
depois do comando para parar os motores.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (false) {
            	
            }
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 21
Duplique o bloco ``||logic:status_SL=7||``
e coloque a cópia no lugar da condição ``||logic:falso||`` do laço.


```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
            	
            }
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
## Passo 22
Copie a chamada da função ``||functions:ligar seguidor_linha|`` e cole dentro do
``||loops:enquanto executar|``.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
            }
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 23
Duplique o bloco ``||FuzzyBoT:Motor esquerdo mover para frente com velocidade 50||``
e coloque a cópia abaixo da chamada da função ``||functions:ligar seguidor_linha||``.
Troque o sentido de frente para **trás**.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
            }
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
## Passo 24
Repita o processo do passo anterior para o acionamento do motor direito também alterando o sentido,
criando o bloco ``||FuzzyBoT:Motor direito mover para frente com velocidade 50||``.
O primeiro laço gira o robô no sentido horário por 2.5 segundos ou até encontrar a linha, caso a linha não seja encontrada o segundo laço 
gira o robô no sentido anti-horário até encontrar a linha.
```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 25
Coloque um comando ``||FuzzyBoT:parar motor todos||`` depois do primeiro
``||loops:enquanto executar||``.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
## Passo 26
Precisamos chamar a função que acabamos de criar antes de iniciar o movimento do robô.
Vá ao menu ``||Advanced:Avançado||``, acesse ``||functions:Funções||`` e selecione o bloco
``||functions:encontra linha||``. Posicione o bloco no início da entrada ``||input: no botão B pressionado||``. 

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 27

Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:conta_e_vira||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.
Essa função tem o objetivo de contar por quantas esquinas o robô passa e virar 90° à direita em cada uma delas.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
	
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 28
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:esquinas||``.
Pegue o bloco ``||variables:alterar esquinas por 1||`` e coloque-o no começo da função recém criada.
```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 29
Adicione o bloco ``||FuzzyBoT:Motor esquerdo mover para frente com a velocidade 0||``
diretamente da aba ``||Fuzzybot:Fuzzybot||``. 
Modifique o valor da velocidade para **40**.
```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 30

Duplique o bloco adicionado do passo anterior e coloque a cópia logo embaixo do mesmo.
Altere o motor para **direito** e o sentido para **trás**, criando o bloco
``||FuzzyBoT:Motor direito mover para trás com velocidade 40||``.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 31

Acesse a aba ``||loops:Loops||`` e adicione um bloco ``||loops:enquanto executar||``
abaixo do acionamento dos motores.


```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (false) {
    	
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
## Passo 32

Copie o comparador ``||logic:status_SL=7||`` do laço ``||loops::enquanto executar||``
e cole dentro do novo laço no lugar da condição ``||logic:falso||``.


```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
    	
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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


## Passo 33

Acesse o menu de ``||Functions:Funções||``, dentro de ``||Advanced:Avançado||``
e adicione o comando ``||Functions:ligar seguidor_linha||``
dentro do laço.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
        seguidor_linha()
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 34

Vá ao menu ``||basic:Básico||``, e adicione um bloco ``||basic:pausa (ms) 100||``
após a chamada da função. Mude o tempo da pausa para **50**.
Terminamos a construção da função, toda vez que o robô sai da linha em uma esquina ele incrementa a 
variável ``||variables:esquinas||`` e gira o robô no sentido horário até que o sensor toque a próxima linha.


```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
        seguidor_linha()
        basic.pause(50)
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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

## Passo 35

O laço ``||basic:sempre||`` é responsável por verificar a leitura do sensor e determinar
o movimento do robô de acordo com a letirura.
Portanto adicionaremos nele o que fazer quando a letirura do sensor retornar o valor 7,
que indica que o sensor entrou em uma região toda branca, no caso do nosso percurso, uma esquina.
Depois da condicional  ``||logic:se status_SL = 6 então||`` clique no botão **+** duas vezes
para criar outra condicional  ``||logic:senão se então||``.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
        seguidor_linha()
        basic.pause(50)
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
        } else if (false) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})


```

## Passo 36

Copie o comparador ``||logic:status_SL=7||`` do laço ``||loops::enquanto executar||``
e cole dentro da nova condicional no lugar da condição ``||logic:falso||``.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
        seguidor_linha()
        basic.pause(50)
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
        } else if (status_SL == 7) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})



```

## Passo 37

Acesse o menu de ``||Functions:Funções||``, dentro de ``||Advanced:Avançado||``
e adicione o comando ``||Functions:ligar conta_e_vira||``
dentro da condicional.

```blocks
let Iniciar = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
        seguidor_linha()
        basic.pause(50)
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
        } else if (status_SL == 7) {
            conta_e_vira()
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})


```

## Passo 38

Para finalizar programaremos o cálculo e exibição do número de voltas feitas pelo robô.
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:voltas||``.
Arraste um bloco ``||variables:definir volta para 0||`` para a entrada ``||input:no botão A pressionado||``.

```blocks
let Iniciar = 0
let voltas = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
    voltas = 0
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
        seguidor_linha()
        basic.pause(50)
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
        } else if (status_SL == 7) {
            conta_e_vira()
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 39

Vá até o menu ``||math:Matemática||`` busque o bloco ``||math:raiz quadrada 0||``
e coloque-o no lugar do **0** da definição da variável.
Troque a operação de ``||math:raiz quadrada||`` para ``||math:integer /||``,
essa operação retorna a parte inteira da divisão entre os elementos.
```blocks
let Iniciar = 0
let voltas = 0
let contador = 0
let status_SL = 0
let esquinas = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
    voltas = Math.idiv(0, 0)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
        seguidor_linha()
        basic.pause(50)
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
        } else if (status_SL == 7) {
            conta_e_vira()
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 40

Modifique os valores da divisão. Pegue a variável ``||variables:esquinas||``,
coloque no lugar do dividendo e substitua o **0** do divisor por **4**.

```blocks
let Iniciar = 0
let voltas = 0
let esquinas = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
    voltas = Math.idiv(esquinas, 4)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
        seguidor_linha()
        basic.pause(50)
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
        } else if (status_SL == 7) {
            conta_e_vira()
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 41

Por fim volte à seção ``||basic:Básico||`` e utilize o comando ``||basic: mostrar número 0||``
abaixo no fim da entrada ``||input:o botão A pressionado||``. Atualize o valor **0** para a variável
``||variables:voltas||``.

```blocks
let Iniciar = 0
let voltas = 0
let esquinas = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
    voltas = Math.idiv(esquinas, 4)
    basic.showNumber(voltas)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
        seguidor_linha()
        basic.pause(50)
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
        } else if (status_SL == 7) {
            conta_e_vira()
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 42
Agora seu código está pronto! Baixe-o para o micro:bit e posicione o FuzzyBoT sobre o início
do caminho definido pela linha, de forma que ele fique orientado a fazer as curvas para a direita. Pressione o botão B para ele iniciar o movimento. Espere o robô dar algumas voltas para
retirá-lo do circuito e aperte o Botão A, observe a exibição no display do micro:bit do número de voltas.


```blocks
```
## Passo 43
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let Iniciar = 0
let voltas = 0
let esquinas = 0
let contador = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
    voltas = Math.idiv(esquinas, 4)
    basic.showNumber(voltas)
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
    encontra_linha()
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function encontra_linha () {
    while (contador < 50) {
        fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
        fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 50)
        contador += 1
        basic.pause(50)
        seguidor_linha()
        if (status_SL == 0) {
            contador = 50
        }
        if (status_SL == 7 && contador == 50) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
            while (status_SL == 7) {
                seguidor_linha()
                fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 50)
                fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
            }
        }
    }
fuzzyBot.motorStop(fuzzyBot.Motors.All)
}
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
function conta_e_vira () {
    esquinas += 1
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 40)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 40)
    while (status_SL == 7) {
        seguidor_linha()
        basic.pause(50)
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
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
        } else if (status_SL == 7) {
            conta_e_vira()
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```