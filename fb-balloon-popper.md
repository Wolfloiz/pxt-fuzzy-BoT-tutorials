### @diffs true
# Estoura Balões

## Passo 1
Nesse tutorial, vamos adaptar o código do FuzzyBoT controlado pelo Joystick
para transformá-lo em um robô que estoura balões! Para isso, iremos criar 
condições que permitam movimentar um servomotor quando pressionarmos o 
botão A do Joystick.

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
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 2
Para começar, verifique se a biblioteca da Fuzzy Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
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
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 3
Acesse o menu ``||fuzzyBot:FuzzyBoT||`` e insira o comando 
``||fuzzyBot:servo S1 definir para ângulo 0||`` dentro do 
``||basic:no iniciar||``. 

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
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
```

## Passo 4
Acesse a categoria ``||Logic:Lógica||`` e adicione um bloco 
``||Logic:se então||`` dentro do ``||radio:ao receber rádio name value||``.

 **Atenção:** Ele deve ser posicionado abaixo dos outros blocos ``||Logic:se então||``,
 não podendo estar dentro de nenhum deles.

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
    if (true) {
    	
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
```

## Passo 5
Em seguida, retorne à aba ``||Logic:Lógica||`` e utilize o comparador 
``||Logic:0 = 0||`` para substituir o campo ``||Logic:verdadeiro||``.

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
    if (0 == 0) {
    	
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
```

## Passo 6
Clique sobre o bloco redondo ``||variables:name||`` do laço 
``||radio:ao receber rádio name valor||`` e arraste-o para substituir o primeiro
campo do comparador. Em seguida, clique em ``||advanced:Avançado||`` para abrir 
outras categorias de blocos, clique em ``||text:Texto||`` e selecione o bloco 
redondo de aspas duplas: ``||text:" "||``. Posicione-o no segundo campo do 
comparador e escreva a letra **"A"** em seu centro.

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
    if (name == "A") {
    	
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
```

## Passo 7
Retorne à aba ``||Logic:Lógica||`` e adicione um laço 
``||Logic:se então senão||`` **DENTRO** do anterior.

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
    if (name == "A") {
        if (true) {
        	
        } else {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
```

## Passo 8
Retorne à aba ``||Logic:Lógica||`` e use um comparador ``||Logic:0 = 0||`` 
para substituir o campo ``||Logic:verdadeiro||``. O primeiro campo desse 
comparador deve ser o bloco ``||variables:valor||`` retirado do laço 
``||radio:ao receber rádio name valor||``. 

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
    if (name == "A") {
        if (value == 0) {
        	
        } else {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
```

## Passo 9
Dentro desse ``||logic:então||``, adicione um comando
``||fuzzyBot:servo S1 definir para ângulo 0||``, localizado na aba 
``||fuzzyBot:fuzzyBot||``.

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
    if (name == "A") {
        if (value == 0) {
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
        } else {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
```

## Passo 10
Agora, dentro do ``||logic:senão||``, adicione outro comando
``||fuzzyBot:servo S1 definir para ângulo 0||``, porém altere o valor do 
ângulo de **0** para **50**.

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
    if (name == "A") {
        if (value == 0) {
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
        } else {
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, 50)
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
```

## Passo 11

Agora seu código está pronto! Baixe-o para o micro:bit do FuzzyBoT e teste 
o botão A do Joystick para acionar a haste para estourar os balões! 
Lembre-se de ligar ambos os dispositivos e conectá-los no mesmo grupo de rádio.

```blocks
```

## Passo 12
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
    if (name == "A") {
        if (value == 0) {
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
        } else {
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, 50)
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```