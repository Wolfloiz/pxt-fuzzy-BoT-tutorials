### @diffs true
# Prendendo o FuzzyBoT: Parte 2

## Passo 1
Neste projeto, vamos dar continuidade ao uso dos sensores 
infravermelhos do FuzzyBoT adicionando a tela OLED para indicar quantas 
vezes o FuzzyBoT tentou cruzar a linha preta da área ao seu redor. Vamos 
utilizar o código anterior como base e apenas adicionar essas alterações.

```template
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

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, copie o 
endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
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

## Passo 3
Acesse a aba ``||variables:Variáveis||``, e clique em **"Fazer uma variável..."**.
Crie uma variável denominada: ``||variables:tentativas_fuga||``.
Depois de nomeá-la, adicione um bloco 
``||variables:definir tentativas_fuga para 0||``
dentro do bloco ``||basic:no iniciar||``.

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
let tentativas_fuga = 0
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

## Passo 4
Clique na aba ``||fuzzyBot:FuzzyBoT||``. Ao fazer isso, clique no submenu 
que vai se abrir com uma nova aba denominada ``||fuzzyBot:Tela OLED||``. 
Adicione o laço ``||fuzzyBot:Inicializar OLED com largura 128 e altura 64||``
no bloco ``||basic:no iniciar||``. 

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
let tentativas_fuga = 0
fuzzyBot.init(128, 64)
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

## Passo 5
Retorne ao menu ``||fuzzyBot:Tela OLED||`` e adicione o bloco 
``||fuzzyBot:mostrar número 0||`` abaixo do bloco 
``||basic:mostrar ícone||`` dentro do ``||basic:no iniciar||``. 

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
let tentativas_fuga = 0
fuzzyBot.init(128, 64)
basic.showIcon(IconNames.Heart)
fuzzyBot.writeNumNewLine(0)
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

## Passo 6
Retorne à aba ``||variables:Variáveis||`` e utilize o bloco da variável  
``||variables:tentativas_fuga||`` para substituir o valor **0** do comando
``||fuzzyBot:mostrar número||``.

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
let tentativas_fuga = 0
fuzzyBot.init(128, 64)
basic.showIcon(IconNames.Heart)
fuzzyBot.writeNumNewLine(tentativas_fuga)
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

## Passo 7
Agora, clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` 
e clique em **Fazer uma função...**.
Crie uma função chamada ``||Functions:mostra_tentativas||``.
Um novo laço referente à função criada é adicionado automaticamente ao código.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function mostra_tentativas () {
	
}
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
let tentativas_fuga = 0
fuzzyBot.init(128, 64)
basic.showIcon(IconNames.Heart)
fuzzyBot.writeNumNewLine(tentativas_fuga)
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

## Passo 8
Acesse a aba ``||variables:Variáveis||`` e adicione o bloco  
``||variables:alterar tentativas_fuga por 1||`` dentro do bloco da nova função 
``||Functions:mostra_tentativas||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function mostra_tentativas () {
    tentativas_fuga += 1
}
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
let tentativas_fuga = 0
fuzzyBot.init(128, 64)
basic.showIcon(IconNames.Heart)
fuzzyBot.writeNumNewLine(tentativas_fuga)
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

## Passo 9
Retorne à categoria ``||fuzzyBot:Tela OLED||`` e adicione o bloco 
``||fuzzyBot:Limpar display OLED||`` dentro da função 
``||Functions:mostra_tentativas||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function mostra_tentativas () {
    tentativas_fuga += 1
    fuzzyBot.clear()
}
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
let tentativas_fuga = 0
fuzzyBot.init(128, 64)
basic.showIcon(IconNames.Heart)
fuzzyBot.writeNumNewLine(tentativas_fuga)
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

## Passo 10
Adicione o bloco ``||fuzzyBot:mostrar número||`` com o valor da variável 
``||variables:tentativas_fuga||`` dentro da função 
``||Functions:mostra_tentativas||``, como foi feito dentro do 
``||basic:no iniciar||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function mostra_tentativas () {
    tentativas_fuga += 1
    fuzzyBot.clear()
    fuzzyBot.writeNumNewLine(tentativas_fuga)
}
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
let tentativas_fuga = 0
tentativas_fuga = 0
fuzzyBot.init(128, 64)
basic.showIcon(IconNames.Heart)
fuzzyBot.writeNumNewLine(tentativas_fuga)
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

## Passo 11
Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` 
e selecione o bloco ``||Functions:ligar mostra_tentativas||``. Ele deve 
ser posicionado dentro do laço ``||basic:sempre||``, dentro do primeiro 
``||logic:senão||``, antes do bloco de definição da variável 
``||variables:direção||``.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function mostra_tentativas () {
    tentativas_fuga += 1
    fuzzyBot.clear()
    fuzzyBot.writeNumNewLine(tentativas_fuga)
}
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
let tentativas_fuga = 0
tentativas_fuga = 0
fuzzyBot.init(128, 64)
basic.showIcon(IconNames.Heart)
fuzzyBot.writeNumNewLine(tentativas_fuga)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
            mostra_tentativas()
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

## Passo 12
Transfira seu código para o micro:bit e pressione o botão A da placa para 
iniciar a movimentação do robô. Ao cruzar as linhas nas extremidades
da área em que está aprisionado, observe se a contagem de tentativas de 
fuga foi alterada na tela OLED do FuzzyBoT.

```blocks
```

## Passo 13
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.A, function () {
    iniciar = 1
    basic.showIcon(IconNames.Yes)
})
function mostra_tentativas () {
    tentativas_fuga += 1
    fuzzyBot.clear()
    fuzzyBot.writeNumNewLine(tentativas_fuga)
}
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
let tentativas_fuga = 0
tentativas_fuga = 0
fuzzyBot.init(128, 64)
basic.showIcon(IconNames.Heart)
fuzzyBot.writeNumNewLine(tentativas_fuga)
basic.pause(1000)
basic.forever(function () {
    if (iniciar == 1) {
        seguidor_linha()
        if (status_SL == 7) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
        } else {
            mostra_tentativas()
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
