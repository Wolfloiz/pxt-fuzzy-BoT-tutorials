
### @diffs true
# Empilhadeira

## Passo 1
Neste tutorial, criaremos a programação para controlar a estrutura da empilhadeira através de comandos do Joystick.
Para isso, vamos reaproveitar o código da atividade do Veículo controlado pelo Joystick e adicionar a interpretação
dos sinais recebidos ao pressionar os botões A e B para acionar o servomotor.

```template
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 3
Primeiramente, certifique-se de que o Joystick e sua empilhadeira se conectem no mesmo grupo de rádio. 
Utilize o grupo **255** ou qualquer outro próximo desse valor. Em seguida, duplique todo o laço
``||logic:se name = "D" então||`` e posicione o novo laço diretamente abaixo do anterior.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 4
Altere o segundo campo do ``||logic:comparador||`` do ``||variables:name||`` de **"D"** para **"A"**.
Depois disso, exclua ambos os blocos de controle dos ``||fuzzyBot:LEDs||`` dentro do ``||logic:então||`` e ``||logic:senão||`` do laço
lógico do ``||variables:valor||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
        	
        } else {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 5
Antes de prosseguir, clique no sinal de **-** para apagar o laço ``||logic:senão||`` da estrutura
lógica do ``||variables:valor||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 6
Acesse a aba ``||variables:Variáveis||``, e clique em **"Fazer uma variável..."**.
Crie uma variável denominada: ``||variables:angulo||``.
Depois de nomeá-la, adicione um bloco ``||variables:definir angulo para 0||`` dentro deste ``||logic:então||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = 0
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 7
Acesse o menu de ``||math:Matemática||`` e substitua o campo **0** do bloco ``||variables:definir angulo||`` pelo bloco
``||math:constrain 0 between 0 and 0||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(0, 0, 0)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 8
Substitua o primeiro **0** desse bloco pela operação de adição ``||math:0 + 0||``, também localizada
na aba ``||math:Matemática||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(0 + 0, 0, 0)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 9
A primeira parcela dessa adição será a própria variável ``||variables:angulo||`` e a segunda será o número **10**.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 10, 0, 0)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 10
Agora, edite os limites do bloco ``||math:constrain||``, alterando o último **0** por **130**.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 10, 0, 130)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 11
Feito isso, acesse o menu ``||fuzzyBot:FuzzyBoT||`` e adicione o comando ``||fuzzyBot:servo S1 definir para ângulo 0||``
abaixo do bloco de definição da variável.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 10, 0, 130)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 12
Modifique o valor do ângulo de **0** para a variável ``||variables:angulo||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 10, 0, 130)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 13
Duplique todo o laço ``||logic:se name = "A" então||`` e posicione o novo laço diretamente abaixo do anterior.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 10, 0, 130)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 10, 0, 130)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 14
Altere o segundo campo do ``||logic:comparador||`` do ``||variables:name||`` de **"A"** para **"B"**.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 10, 0, 130)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
    if (name == "B") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 10, 0, 130)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 15
Por fim, clique na seta da ``||math:adição||`` para alterar a operação para uma ``||math:subtração||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 10, 0, 130)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
    if (name == "B") {
        if (value == 0) {
            angulo = Math.constrain(angulo - 10, 0, 130)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 16
Agora seu código está pronto! Baixe-o para o micro:bit, certifique-se de "zerar" o servo motor e 
conectar o Joystick e a empilhadeira no mesmo grupo de rádio. Utilize os botões A e B do Joystick
para movimentar o servo para cima e para baixo.

```blocks
```

## Passo 17
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 10, 0, 130)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
    if (name == "B") {
        if (value == 0) {
            angulo = Math.constrain(angulo - 10, 0, 130)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
